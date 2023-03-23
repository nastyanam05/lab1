# lab1
1. Скачать библиотеку boost с помощью утилиты wget. Адрес для скачивания https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz.
$ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz

HTTP-запрос отправлен. Ожидание ответа… 200 OK
Длина: 111710205 (107M) [application/x-gzip]
Сохранение в: «boost_1_69_0.tar.gz»

2. Разархивировать скаченный файл в директорию ~/boost_1_69_0
$ tar -xvf boost_1_69_0.tar.gz

3. Подсчитать количество файлов в директории ~/boost_1_69_0 не включая вложенные директории.
$ find . -maxdepth 1 -type f | wc -l
Ответ: 12

4. Подсчитать количество файлов в директории ~/boost_1_69_0 включая вложенные директории.
$ find . -type f | wc -l
Ответ: 61191

5. Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).
$ find . -name «*.hpp» -o -name «*.h» | wc -l
Ответ: 15208
$ find . -name «*.cpp» | wc -l
Ответ: 13774
$ find . -type f -and -not -name «*.cpp» -and -not -name «*.h» -and -not -name «*.hpp» | wc -l
Ответ: 32209

6. Найдите полный путь до файла any.hpp внутри библиотеки boost.
$ find . -name «any.hpp»
Ответ: 
./boost/fusion/include/any.hpp
./boost/fusion/algorithm/query/any.hpp
./boost/fusion/algorithm/query/detail/any.hpp
./boost/spirit/home/support/algorithm/any.hpp
./boost/proto/detail/any.hpp
./boost/type_erasure/any.hpp
./boost/hana/fwd/any.hpp
./boost/hana/any.hpp
./boost/any.hpp
./boost/xpressive/detail/utility/any.hpp

7. Выведите в консоль все файлы, где упоминается последовательность boost::asio.
$ grep -rl ‘boost::asio’ (grep - поиск строки в файлах, -l - вывод только имени файла, -r - рекурсивный поиск)

8. Скомпилируйте boost. Можно воспользоваться инструкцией или ссылкой.

cd tools/build
./bootstrap.sh (создание конфигурации сборки)
./b2 install --prefix=test (скомпилировать файлы)
Ответ:
...updated 436 targets...

9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs
mkdir ~/boost-libs (создание папки boost-libs)
mv * ~/boost-libs (перенос всех файлов)

10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
cd ~/boost-libs/ (переход в папку с файлами)
du -s (размер выводится в кб по умолчанию)

11. Найдите топ10 самых "тяжёлых".
du -s * | sort -nr | head (-n - по числовым значениям, -r - в рекурсивном порядке, head - выводит первые строки, по умолчанию 10)
