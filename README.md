# BitTorrent-Client

<p>
I am trying to implement a BitTorrent Client from scratch .This attempt uses C++ language. I will keep 
documenting the implementation details in this markdown file.
</p>

<p>
I find this particular project intriguing because it is an application of Distributed Systems and I am very excited to learn and build this!
</p>

<p>
I will briefly describe how I understand the things:
</p>

<ul>
<li>Peers are users/entities who own pieces/parts of the file that we need to download.</li>
<li>The list of peers who own pieces of the file is maintained on an entity called the 'Tracker'.</li>
<li>So we first request this list from the Tracker and then proceed to request file pieces from these particular set of peers.</li>
<li>Then assemble these pieces into a single file and (disconnect) from the Network!</li>
</ul>

<ul>
<li>The user starts with a .torrent file or a magnet URI . We are expected to extract the info hash from this.</li>
<li>Then we request peerlist from the 'Tracker' by sending this infohash-details.</li>
</ul>

To elaborate how the requesting procedure should take place :-
<ul>
<li>If the user already has a .torrent file with them , then the client has to decode the Bencoded dictionary and then make a request to the announce URL</li>
<li>Else if the user has a magnet URI then-
<ul>
<li>If neither address tracker nor the peers are present then we have to proceed to download directly from any acceptable source or else we return a failure message</li>
<li>If address tracker is absent but list of peers is available then we can simply go ahead and make a request to every peer for the file pieces</li>
<li>If the address tracker is present then we should go ahead and fetch the (array of) trackers in parameter tr and send a request to each of these tr URLs.</li>
</ul>
</li>
<li>Lastly choose a peer to connect to</li>
</ul>

<p>
Info hash is sha-1 encoding of a part of the contents of the .torrent file.
Peer id is simply the id of a peer on the network.
</p>

<p>
How Bencode works:
- `integer = i<integer>e`
- `byte string = <length>:<contents>`
- `lists = l<elements>e`
- `dictionaries = d<pairs>e`

</p>

<p>
Both .torrent file and the magnet URI contain info hash and peer id. Only the .torrent file consists of the announce(url of tracker). And only the magnet URI contains the address tracker, peer,acceptable source and so on...
</p>
