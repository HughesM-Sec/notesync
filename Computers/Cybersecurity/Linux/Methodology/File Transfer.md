You can use python to start an http server and transfer files using wget.

Host the server:
	**python3 -m http.server** *PORT*

Extract the file:
	**wget** *IP:PORT FILE*



You can also use the **scp** command to transfer to and from via *ssh*.

	scp user@IP_ADDRESS:/file/location/here.txt /file/destination/here

You can also transfer a file to a remote host via *ssh*.

	scp /file/location/here.txt user@IP_ADDRESS:/file/destination/here

