# Binarybeast

This is a Ruby Gem to access the BinaryBeast.com API. It was extracted from the [Gamkoi.com](http://www.gamkoi.com) Source Code and was written by Crispin Schäffler

## Installation

Add this line to your application's Gemfile:

    gem 'binarybeast'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install binarybeast

## Usage

    @tourney = Binarybeast::Tourney.new

there are several options you can use when creating a tourney:

    :title => String
    :description => String
    :public => Integer
    :game_code => String
    :type_id => Integer
    :elimination => Integer
    :team_mode => Integer
    :group_count => Integer
    :teams_from_group => Integer
    :location => String
    :max_teams => Integer
    :replay_uploads => Integer
    :replay_downloads => Integer
    :auto_start => Integer
    :return_data => Integer

however, only :title => String is required for creating a new tourney object.

## Create a new Tournament on BinaryBeast

    @tourney = Binarybeast::Tourney.new(:title => "Test Tournament", :description => "This comes from a ruby gem accessing your api.")
    @tourney.create
    
## Fetching a existing Tournament from BinaryBeast

    @tourney = Binarybeast::Tourney.load(:id => "xSC21212194")

## Current implemented Functions

This is a pre release of the gem soon to be. Current functions include

    .new
    .create
    .update
    .load
    .delete
    .setBuild
    .setConfirmation
    .start

more to come soon....

## Some stuff you should know

### :force => true

The BinaryBeast API sends back JSON from every request. However, if you use this gem we catch the JSON Data and proccess it. If you want to have a direct access to the API you can go with something like this:

    @tourney = Binarybeast::Tourney.new(:title => "Test")
    response = @tourney.create(:force => true)
    
the :force => true tells the function to give you the callback from the binarybeast directly. The response is now a parsed hash, so this will work

    response["Result"]
    => 200

## Changelog

### Version: 0.1.3.pre

* Added Eigenclass to Tourney, so you can call Binarybeast::Tourney.load(:id => "").
* Changed variable names to use underscore naming convention rather than all lower case naming.
* Added a call function to the Binarybeast module. You are now able to call Binarybeast.call() to make a raw API call to Binarybeast. Returns a JSON parsed array.
