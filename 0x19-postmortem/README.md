## Postmortem

The `0x19-postmortem` project was released at exactly 6:00 AM(WAT) on 31 October, 2022. The ubuntu 14.04 container running on Apache web server was returning a `500 Internal Server Error` when a GET request was made. The expected output was a HTML file defining a simple Holberton WordPress site.
## Debugging

Junior Software developer on duty as at the time of this error was [Uche](https://github.com/Kinguche2) and he promptly proceeded to solve the problem.

1. The running process was accessed first using `ps aux` and two `apache2` processes - `root` and - `www-data` - were properly running.

2. The `sites-available` folder of the `/etc/apache2/` directory showed that the web server was serving content located in `/var/www/html/`.

3. Then he ran `strace` in one terminal on the PID of the `www-data` Apache process and in another terminal, curled the server using `curl sI <localhost ip>`. Strace revelead an `ENOENT (No such file or directory)` error ocuring when the file `var/www/html/wp-includes/class-wp-locale.phpp` was being accessed.

4. [Uche](https://github.com/Kinguche2) proceeded to check each file in the `/var/www/html/` directory to find the erroneous `.phpp` file extension. the extension was located in the `wp-settings.php` file (line 137).

5. The trailing `p` was removed from the line.

6. Another `curl` test was made on the server and it returned a 200 A-ok!

7. A puppet manifest was made to automate fixing of the error.

##Summary

A typo error was the bug in this case and removing of the trailing `p` allowed the WordPress app to locate the correct file.

This error could have been prevented if testing was done on the application before it was deployed. Also, status monitoring could be enabled by setting up an automated uptime-monitoring services like [UptimeRobot](https://uptimerobot.com/) to instantly alert upon outage of the website

Note that in response to this error, I wrote a Puppet manifest [0-strace_is_your_friend.pp](https://github.com/kinguche2/alx-system_engineering-devops/0x17-web_stack_debugging_3/0-strace_is_your_friend.pp) to automate fixing of any such identitical errors should they occur in the future. The manifest replaces any phpp extensions in the file /var/www/html/wp-settings.php with php.
