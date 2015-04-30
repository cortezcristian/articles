Search Freq
/opt/pythonenv/v2_ordergroove-py27/static/js$ find ./ -name freq* | xargs grep weeks

Replace
find ./ -type f -exec sed -i 's/5% off/10% off/g' "{}" +;




find ./ -type f -exec sed -i 's#Test Game#Unit Tests#g' "{}" +;
