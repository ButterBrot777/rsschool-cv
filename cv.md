### Pavel, Karenda
##### E-mail: korendos@gmail.com
##### I want to be a web-developer because I like this profession. 

###### It corresponds to my conception about ideal work:
     - great opportunities for professional growth
     - better working atmosphere
     - polite communities
     - many friends with common interests
   I am a **mature** person and I know what I want. 
   I am good at getting on with people. I quickly find the information I need. 
   I am **diligent and purposeful**.

#### My skills are:

##### * Programming languages and skills:
    
      - Pascal
      - Fortran 90
  	  - HTML
  	  - CSS
  	  - JavaScript
#####  * Version control:
   	 - Git 
#####  * Methodologies:
     - Scrum & Agile SDM
##### * Tools:
     - WebStorm, Visual Studio Code, Figma

#### Code examples: 
	<!-- BEGIN CODE example -->
	<!-- This program collects gem-statistics for Ruby. It parses the github site for such parameters as "watchers", "stargazers", used_by etc. and gives a list of them. -->
	<!--# frozen_string_literal: true-->

	require 'yaml'
	require 'open-uri'
	require 'bundler/setup'
	require './main.rb'
	Bundler.require

	<!--# for parsing HTML-->
	class Parser
	  def get_gem_url(gem_name)
	    url = URI("https://github.com/search?q=#{gem_name}")
	    html = Kernel.open(url).read
	    doc = Nokogiri::HTML(html)

	    gem_url = doc.xpath("//ul[@class='repo-list']/li//a").first['href']

	    @url_used_by = URI("https://github.com/#{gem_url}/network/dependents")
	    

	    "https://github.com#{gem_url}"
	  end

	  def get_gem_data(gem_name)
	    gem_url = get_gem_url(gem_name)
	    html = Kernel.open(gem_url).read
	    doc = Nokogiri::HTML(html)
	    html_used_by = Kernel.open(@url_used_by).read
	    doc_used_by = Nokogiri::HTML(html_used_by)

	    result = {}
	    result[:watch] = doc.xpath("//a[contains(@href, 'watchers')]").text.strip.to_i
	    result[:star] = doc.xpath("//a[contains(@href, 'stargazers')]").text.strip
	    result[:fork] = doc.xpath("//a[contains(@href, 'network/members')]").text.strip

	    result[:contributors] = doc.css(".text-emphasized")[3].text.strip.to_i
	    result[:issue] = doc.css(".Counter")[0].text.strip.to_i
	    result[:used_by] = doc_used_by.css('.btn-link')[1].text.gsub(/\D/, '').to_i

	    result
	  end

	  gems = YAML.load_file('gems.yml')
	  parser = Parser.new

	  gems['gems'].each do |gem_name|
		puts parser.get_gem_data(gem_name)
		sleep 1
	  end

	end
	<!-- END CODE example -->

#### Professional experience: no

#### Courses:
##### - Rubizza Surviving Camp course (_not completed_)
##### - [HTMLacademy.ru](https://HTMLacademy.ru) - online course HTML and CSS
##### - [Learn.javascript.ru](http://learn.javascript.ru) - online tutorial for learning JavaScript language

#### Language skills:
	 - English: A2
	 - German: B1
	 - Polish: B2
