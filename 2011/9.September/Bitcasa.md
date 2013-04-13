{"title":"Buyer Beware of Bitcasa", "date":1316026480000}
++++++++++
I was reading Ben Brooks's [Death Spiral](http://brooksreview.net/2011/09/death-spiral/) post and caught mention of [Bitcasa](http://www.bitcasa.com/), an unlimited (“Infinite”) storage provider. They popped up on my [TechCrunch feed yesterday](http://techcrunch.com/2011/09/12/with-bitcasa-the-entire-cloud-is-your-hard-drive-for-only-10-per-month/) but I didn't pay them much mind.[^1]

Skimming the article I found a pair of conflicting passages:

> But Bitcasa is not like any of those services. It doesn't move files around. It doesn't sync files. It deals in bits and bytes, the 1's and 0's of digital data.
>
> When you save a file, Bitcasa writes those 1's and 0's to its server-side infrastructure in the cloud. It doesn't know anything about the file itself, really. It doesn't see the file's title or know its contents. It doesn't know who wrote the file. And because the data is encrypted on the client side, Bitcasa doesn't even know what it's storing.

[Sarah Perez](http://techcrunch.com/author/sarah-perez/) dumbs down encrypted storage for us. Bitcasa supposedly performs some clientside encryption prior to uploading the files. This would make your files *unique and completely unrecoverable without your specific key*.

Continuing on we find the truth behind that bullet proof encryption process might be little stretched.

> And the pricing! How on earth is it so cheap?
>
> That's the easy part, actually. Explains Bitcasa CEO Tony Gauda, $10/month still gives the company large margins. **The fact is, 60% of your data is duplicate.** If you have an MP3 file, someone else probably has the same one, for example. Each person only tends to have around 25 GB of unique, personal data, he says. Using patented de-duplication algorithms, compression techniques and encryption, Bitcasa keeps costs down (way, way down, but that's it's secret sauce), which is what makes it so affordable. Bitcasa also explained that a freemium model is on its way with less-than-unlimited storage for free.

Emphasis mine. Bitcasa is checking to see if any files you are uploading match files already uploaded. This is the same thing Dropbox does to try and cut down on the amount of data they actually have to store.

> Dropbox tries to be very smart about minimizing the amount of bandwidth used. If we detect that a file you're trying to upload has already been uploaded to Dropbox, we don't make you upload it again. Similarly, if you make a change to a file that's already on Dropbox, you'll only have to upload the pieces of the file that changed.

<cite>Source: [Dropbox Forums](http://forums.dropbox.com/topic.php?id=13313#post-83928)</cite>

This process of minimizing data transfer by examining what already exists is called [data de-duplication](http://www.backupcentral.com/mr-backup-blog-mainmenu-47/13-mr-backup-blog/134-inline-or-post-process.html/). If Bitcasa is using this to minimize transfer and total storage then they do have access to the blocks, chunks, or whole files as in order for de-duplication to work you have to compare two similarly encrypted files. If they have two similarly encrypted files then they are able to decrypt the files as they are not using anything specific to a user. If they were de-duplication would not be possible.

[^1]: I'm a [Dropbox guy](http://joshuakehn.com/2011/1/6/Dropbox-Evernote-and-Instapaper.html#dropbox).