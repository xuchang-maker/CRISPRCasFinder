# CRISPRCasFinder
一个没有root权限的CRISPRCasFinder软件的安装教程

wget -c https://github.com/dcouvin/CRISPRCasFinder/archive/master.zip

sed -i "s/sudo//g" installer_UBUNTU.sh #将sudo去除

sh installer_UBUNTU.sh

perl CRISPRCasFinder.pl -h #缺少模块

perl -MCPAN -e 'install Date::Calc'
locate Date/Calc.pm #或者将你缺少的模块直接移动到~/perl5/lib/perl5，然后直接export PERL5LIB=~/perl5/lib/perl5
export PERL5LIB="/home/cheng/.cpan/build/Unix-Sysexits-0.06-0/blib/lib:/home/cheng/.cpan/build/Unix-Sysexits-0.06-0/lib:/home/cheng/.cpanm/work/1592559386.15556/Unix-Sysexits-0.06/blib/lib:/home/cheng/.cpanm/work/1592559386.15556/Unix-Sysexits-0.06/lib"
perl -e 'use Date::Calc' #不报错表示模块安装成功

perl CRISPRCasFinder.pl -h #缺少依赖软件

#vmatch2，mkvtree2，vsubseqselect2在src或者bin路径可以找到
cp vmatch2 /home/xuchang/perl5/bin/
cp mkvtree2 /home/xuchang/perl5/bin/
cp vsubseqselect2 /home/xuchang/perl5/bin/

#fuzznuc和needle需要下载emboss
wget ftp://ftp.ebi.ac.uk/pub/software/unix/EMBOSS/EMBOSS-6.6.0.tar.gz 
cp fuzznuc /home/xuchang/perl5/bin/
cp needle /home/xuchang/perl5/bin/

#可能会缺少muscle
wget http://drive5.com/muscle/downloads3.8.31/muscle3.8.31_i86linux64.tar.gz #下载完后需要重命名并移动
cp muscle3.8.31_i86linux64 /home/xuchang/perl5/bin/muscle

perl CRISPRCasFinder.pl -in install_test/sequence.fasta -cas -cf CasFinder-2.0.3 -def G -keep
