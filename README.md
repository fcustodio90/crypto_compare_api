# CryptoCompareApi

Welcome to CryptoCompareApi Gem! This gem is designed to fetch information from https://www.cryptocompare.com/ using built in methods. It uses RESTClient API but don't worry everything will be installed for you.

This gem is 100% open source which means anyone can contribute to it or open issues if bugs are found or wish to add extra functionality to it.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'crypto_compare_api'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install crypto_compare_api

If you are prompt with install errors run:

    $ bundle update

Also this gem will work without an API key but it is recommended that you create one at https://www.cryptocompare.com/ 

After creating your profile and generating a new key do:

    $ touch .env

and copy paste your key like this:

    CRYPTO_COMPARE_API_KEY = your_key

## Usage

This gem works as a service so anytime you wanna call a built in method you need to type -> CryptoCompareApi::CryptoCompareApi.new.INSERT_METHOD

It packs with the following methods:

The initialize 

Everytime you create an instance of CryptoCompareApi the constructor creates an empty string, an empty array and the base urls used for the specific methods built in. This is designed this way because CryptoCompareApi uses different urls to fetch different information which doesn't have an easy turnaround simply by changing the RestClient query params.

The CRYPTO_HASH comes with 41 cryptocurrencies which are the following: 

    CRYPTO_HASH = {
      Bitcoin: 'BTC',
      Ripple: 'XRP',
      Ethereum: 'ETH',
      Stellar: 'XLM',
      BitcoinCash: 'BCH',
      Eos: 'EOS',
      Litecoin: 'LTC',
      Cardano: 'ADA',
      BinanceCoin: 'BNB',
      Siacoin: 'SC',
      Zcash: 'ZEC',
      EthereumClassic: 'ETC',
      Aeternity: 'AE',
      Iota: 'IOT',
      OmiseGO: 'OMG',
      Neo: 'NEO',
      Icon: 'ICX',
      Tron: 'TRX',
      Nano: 'NANO',
      Monero: 'XMR',
      Ox: 'ZRX',
      DigiByte: 'DGB',
      Zilliqa: 'ZIL',
      Decentraland: 'MANA',
      VeChain: 'VET',
      Gifto: 'GTO',
      Qtum: 'QTUM',
      Waves: 'WAVES',
      Augur: 'REP',
      Stratis: 'STRAT',
      OKEX: 'OKB',
      Dash: 'DASH',
      BitcoinSV: 'BSV',
      Tether: 'USDT',
      NEM: 'XEM',
      Dogecoin: 'DOGE',
      Tezos: 'XTZ',
      TrueUSD: 'TUSD',
      USDCoin: 'USDC',
      BitcoinGold: 'BTG',
      BasicAttentionToken: 'BAT',
      Paxos: 'PAX'
    }

But fear not young padawan! If you want to add a cryptocurrency that is not there we'll get there in just a few seconds! :)

Fast forward, this is a demonstration of how you should use it and the results you'll get once you call the methods.

CryptoCompareApi::CryptoCompareApi.new.call_current.prices

    THIS WILL RETURN AN HASH OF HASHES LIKE THIS
    {"Bitcoin"=>{"BTC"=>3443.67}, "Ethereum"=>{"ETH"=>200.04}}

CryptoCompareApi::CryptoCompareApi.new.call_historical_prices('BTC','daily')

    THIS RETURNS AN ARRAY LIKE THIS
    [8.59, 8.29, 7.75, 7.96, 7.33, 6.77, 6.29, 6.36, 6.9, 5.92, 6.25]

    Note that the first argument passed into the method is the ticker code of the cryptocurrency and the second one will define the timeframe. The smaller the timeframe the bigger the array. This is designed so you can then build charts if you want to. Also the smaller the index the older the price.

    The timeframes you can use are -> 'daily', 'hourly', 'minutely'

CryptoCompareApi::CryptoCompareApi.new.call_latest_news

    This will return a bunch of information ! From urls to pictures, descriptions etc etc. The result is an array of hashes with news articles so feel free to use whatever fits your needs!

CryptoCompareApi::CryptoCompareApi.new.call_top5_traded 

    this will return something like this
    {:Bitcoin=>"BTC", :Ethereum=>"ETH", :EOS=>"EOS", :XRP=>"XRP", :ZCash=>"ZEC"}
    Also this is top5 by 24 HOURS VOLUME AROUND THE WORLD not based on your app! Keep a reminder of that. This has nothing to do with the CRYPTO_HASH that comes with the gem.

CryptoCompareApi::CryptoCompareApi.new.call_top5_winners
        
    this returns an hash like this
    {"REP"=>8.108108108108116, "WAVES"=>6.535947712418292, "BNB"=>4.228486646884287, "BAT"=>2.183984116479158, "QTUM"=>1.8749999999999878}
        
    Also, this is only for top5 winners that are inside the Crypto_Hash of the gem. And as a bonus it is sorted for you from biggest winner to smallest winner because why not !

CryptoCompareApi::CryptoCompareApi.new.call_top5_losers

    this returns an hash like this
    {"DIG"=>-22.26890756302521, "BCH"=>-4.433786825878439, "ZEC"=>-4.110072323161049, "XLM"=>-3.729401561144838, "LSK"=>-3.361344537815129}
  
    As you can guess it works just like the top5 winners! 

And Last but not Least, we don't want you to only use the default cryptocurrencies. So there's a method you can use to add the cryptocurrency you want just make sure to follow the right rules!

CryptoCompareApi::CryptoCompareApi.new.add_crypto_to_hash('NEM','XEM')

    Make sure you add the correct ticker name and ticker code. And that's it!

This is my first gem and it was pulled from a project service I made. So any criticism or contribution is very welcomed!

## Development

After checking out the repo, run `bin/setup` to install dependencies. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/fcustodio90/crypto_compare_api. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).

## Code of Conduct

Everyone interacting in the CryptoCompareApi project’s codebases, issue trackers, chat rooms and mailing lists is expected to follow the [code of conduct](https://github.com/[USERNAME]/crypto_compare_api/blob/master/CODE_OF_CONDUCT.md).
