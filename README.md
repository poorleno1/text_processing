1. Download content from server:
 wget --mirror --convert-links --adjust-extension --page-requisites --no-parent http://episkopat.pl

2. Process 

cd /home/ubuntu/episkopat.pl
egrep -r -i -w 'dewiza|urodzony|święcenia|class="title"' *kardynal-*/* *biskup-*/* | grep -v zdrowa | grep -v 'grzegorz-mizinski/' | sed  -e 's:/index.html::g' | sed -e 's/< li>//g'| sed -e 's:</li>::g' | sed -e 's:<p class="title"><strong>::g' | sed -e 's:</strong></p>::g' | sed -e 's:<p class="motto">::g' | sed -e 's:<br />::g' | sed -e 's:\t::g' | sed -e 's:-2::g' | sed -e 's:<p  class="title">::g' | sed -e 's:</strong>::g' | sed -e 's:</p>::g' | sed -e 's:<p>::g' | sed -e 's/<span style="font-size: small;">//g' | sed -e 's:</span>::g' | grep -v "dzisiaj-swiatu-potrzeba-swiadkow-chryst usa-wywiad" | sed -e 's:&#8211;:-:g' | grep -v "ingres-w-zamosciu-11-sierpnia"> /vagrant/out2.txt

3. Process once again:

/vagrant/swiecenia > /vagrant/swiecenia.csv
/vagrant/urodziny > /vagrant/urodziny.csv
