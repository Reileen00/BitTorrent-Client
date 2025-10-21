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
<ul>

