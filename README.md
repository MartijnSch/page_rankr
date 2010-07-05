# PageRankr

Provides an easy way to retrieve Google Page Rank, Alexa Rank, and backlink counts.

## Get it!

    gem install PageRankr
    
## Use it!

    require 'page_rankr'

### Backlinks

Backlinks are the result of doing a search with a query like "link:www.google.com". The number of returned results indicates how many sites point to that url.

    PageRankr.backlinks('www.google.com', :google, :bing) #=> {:google=>161000, :bing=>208000000}
    PageRankr.backlinks('www.google.com', :yahoo)         #=> {:yahoo=>256300062}
    
If you don't specify a search engine, then all of them are used.

    # this
    PageRankr.backlinks('www.google.com') 
        #=> {:google=>23000, :bing=>215000000, :yahoo=>250522337, :altavista=>137000000, :alltheweb=>74500000, :alexa=>727036} 
    
    # is equivalent to
    PageRankr.backlinks('www.google.com', :google, :bing, :yahoo, :altavista, :alltheweb, :alexa)
        #=> {:google=>23000, :bing=>215000000, :yahoo=>250522337, :altavista=>137000000, :alltheweb=>74500000, :alexa=>727036} 

You can also use the alias `backlink` instead of `backlinks`.
Valid search engines are: `:google, :bing, :yahoo, :altavista, :alltheweb, :alexa`.

### Ranks

    PageRankr.ranks('www.google.com', :alexa, :google) #=> {:alexa=>1, :google=>10}
    
    # this also gives the same result
    PageRankr.ranks('www.google.com')                  #=> {:alexa=>1, :google=>10}

You can also use the alias `rank` instead of `ranks`.
There are two valid rank trackers supported: `:alexa, :google`.
Alexa ranks are descending where 1 is the most popular. If a site has an alexa rank of 0 then the site is unranked.
Google page ranks are in the range 0-10 where 10 is the most popular. If a site is unindexed then the rank will be -1.


## Note on Patches/Pull Requests
 
* Fork the project.
* Make your feature addition or bug fix.
* Add tests for it. This is important so I don't break it in a
  future version unintentionally.
* Commit, do not mess with rakefile, version, or history.
  (if you want to have your own version, that is fine but bump version in a commit by itself I can ignore when I pull)
* Send me a pull request. Bonus points for topic branches.

## TODO
* <del>Get backlink counts for:</del>
  * <del>Google</del>
  * <del>Bing</del>
  * <del>Yahoo!</del>
  * <del>AltaVista</del>
  * <del>AllTheWeb</del>
  * <del>Alexa</del>
* <del>Get Google Page Rank</del>
  * <del>Implement Hashing Algorithm</del>
* <del>Get Alexa ranking</del>
* Major refactorings (Version 2)

## Shout Out
Gotta give credit where credits due!

* http://github.com/alexmipego/PageRankSharp
* http://snipplr.com/view/18329/google-page-range-lookup/
* http://www.sitetoolcenter.com/free-website-scripts/ajax-pr-checker.php 

## Copyright

Copyright (c) 2010 Allen Madsen. See LICENSE for details.