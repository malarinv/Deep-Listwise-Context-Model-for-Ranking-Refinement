mkdir bin;cd bin;
wget http://download.joachims.org/svm_rank/current/svm_rank.tar.gz
tar -xcvf svm_rank.tar.gz
make
cd ../
cd "scripts/Yahoo Letor/SVMrank"
python initial_ranking_with_svm_rank_yahoo.py ../../../bin/ set1.train.txt set1.valid.txt set1.test.txt ./
python Prepare_yahoo_letor_data_set1.py  . ./ ./ 5
cp -r ./ ../../../tmp/
cd ../../../tmp/
rm set1.*
cd ../
python DLCM/main.py
