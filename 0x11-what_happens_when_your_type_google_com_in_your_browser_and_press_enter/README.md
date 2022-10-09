Answering the Web Infrastructure Question: What Happens When You Type a web address(URL) like https://www.google.com Into a Browser and Hit Enter?

This classic web infrastructure question seems to be easy at first for web Developers until they are asked to explain all the tiny details of how it all works. You might be trying to answer it too right now and probably finding yourself stuck at some point. Fret not my friend, because this article is here to give you a detailed, fun and memorable answer to this question and perhaps help you understand something you’ve been missing.

Now, the URL might be something other than https://www.google.com You might type in example.com or something.org or any valid web address. The steps behind typing them into a browser, hitting enter and getting a feedback is quite the same. I’ll be explaining each step, but first…

I’d like us to explain a few terms first so that you don’t get confused when i use them in this article:

    Server: Another word for a computer or computer program. Can refer to either hardware or software. Servers provide functionality for other devices. In the context of this article, usage of the term “server(s)” will refer to the computer system(s) hosting www.google.com
    Client: Also a computer or computer program, but one that can access services and functionalities hosted on a server. Most familiarly, clients are the personal devices — laptops, smartphones, etc. — that we use to access services through the internet, among other things. In the context of this article, usage of the term “client” will refer to the web browser.
    Protocol: Or, more specifically, communication protocol — a general term for a system of rules, or method, for transmitting data between two devices. The Open System Interconnections (OSI) model, the conceptual model used to describe telecommunications between computers, consists of a myriad of protocols.

First step — URL Parsing

Web browsers are rendering engines. Their job is to download a web page and render it in a way that is understandable by a human being. Servers have Internet Protocol(IP) addresses that browsers work on in order to access the servers. Considering the fact that the web is so large, humans find it hard to remember these unique addresses for each URL they make use of. Domain Name System(DNS) makes it possible to assign words and human readable texts to these IP addresses and the browsers probe these string of texts to resolve them to an address.

so when you type in the URL text, the browser separates the text into distinct components in order to parse.

The components for our URL is parsed into the following:

    Protocol — https— the data transfer method to be used between the client and server. In this case, the protocol is HTTPS (HyperText Transfer Protocol Secure).
    hostname — www.google.com is the domain name that points to the IP address of the host server
    port — this is the port on the server our request will be sent through. Not written out in our URL but implied as port 443 because of the type of protocol(https)
    path-and-file-name — This is the path to the file requested for in the servers directory. Also not included in our URL and so we are requesting the root directory of the server.
