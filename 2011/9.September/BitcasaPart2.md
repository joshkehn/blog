{"title":"Bitcasa Saga Continues", "date":1316399558000}  
++++++++++  
[Convergent Encryption][techcrunch] is the "secret sauce" behind the [Bitcasa debate][bitcasa pt1] that I talked about last week. A [helpful fellow on Twitter][twitter] linked to an [interesting paper][pdf] earlier in the week. Now Bitcasa's CEO Tony Gauda has come forward to give us the details on how things are actually being handled data wise.

> OK, so convergent encryption….what happens is when you encrypt data, I have a key and you have a key. And let’s say that that these are completely different. Let’s say that we both have the exact same file. I encrypt it with my key and you encrypt it with your key. Now the data looks completely different because the encryption keys are different. Well, what happens if you actually derive the key from the data itself? Now we both have the exact same encryption key and we can de-dupe on the server side.

There is a line of truth to what he says in the presentation. There is no way for Bitcasa to decrypt your files. However, that does **not** mean your files are secure. Because the convergent encryption process yields blocks that are identical, you can upload content and then figure out if that content is being stored. You don't need to know by who owns the file either. Just send a take down notice to Bitcasa and they remove the chunk.

I don't know if Bitcasa has any methods in place to handle this, especially since the way chunks are linked to users is a little fuzzy. If that relationship can be uncovered then it poses a greater risk of exposing users. 

My recommendation for a truly unlimited solution is still [BackBlaze][bb].

[bitcasa pt1]: http://joshuakehn.com/2011/9/14/Buyer-Beware-of-Bitcasa.html
[techcrunch]: http://techcrunch.com/2011/09/18/bitcasa-explains-encryption/
[twitter]: http://twitter.com/#!/adrianpike/status/114439412829523970
[pdf]: http://www.ssrc.ucsc.edu/Papers/storer-storagess08.pdf
[bb]: http://www.backblaze.com/