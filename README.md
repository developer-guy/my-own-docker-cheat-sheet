##DOCKER CHEAT SHEET##
1 - docker version --> Docker'ın hem server hem client için bilgiler döner.
2 - docker pull image_name:tag_name --> Belirtilen image'ın belirtilen tag ismine sahip olanı DockerHub'dan bizim için localimize indirir.Default olarak ilgili image'ın latest tagli olan halini indirmeye ayarlanmıştır.
3 - docker images --> Localimizde sahip olduğumuz imagelerin listesini döner.
4 - docker run image_name:tag_name --> İmage ismi ve tag ismine sahip olan Image'dan bir container ayağa kaldırır.İlk olarak imageyi localde arar yoksa DockerHub üzerinden imageyi çekmeye çalışır.-d parametresi ile detached
modda çalıştırılabilir bu ilgili image çalıştırılırken çıktıların console yansıtılmasını engeller,bu tip containerlerın çıktılarını görebilmek için docker logs container_id çalıştırılır.
5 - docker ps --> Çalışır durumdaki Containerların bilgisini bize döner.
6 - docker ps -a --> Durumsuz(çalışan veya çalışıp işini tamamlamış olan) olarak bütün Containerların bilgisini döner.
7 - docker start -a container_id --> Belitilen container_id'sine sahip olan container'ın tekrardan console attach edilerek(bağlanarak) çalıştırılmasını sağlar.
Yani eğer imagenız bir çıktı sunuyorsa ilgili container tekrardan start edildiği zaman bu çıktının gözükebilmesi için -a parametresi gereklidir.
8 - docker inspect --format="{{.Id}}" contanier_name --> Belitilen contaner isminin sadece id bilgisini döner.
9 - docker rm container_id --> Belirtilen container_id'ye sahip containerı siler.Eğer -f(force) parametresi ile kullanılırsa çalışır haldeki bir container durdurulmaya zorlanarak silinir.
10 - docker stop container_id --> Belirtilen container_id'ye sahip containerı durdurur.
11 - docker exec -it container_id /bin/bash --> container_id'si belirtilen containerı terminalde açar.
12 - docker kill container_id --> container_id'si belirtilen containerı acil çıkışa zorlar.
13 - docker logs -f container_id -> ontainer_id'si belirtilen containerın çıktılarını dinler.-f(follow)
14 - docker build docker_file_path --> Belitilen yol içerisindeki DockerFile'dan yeni bir image build eder.Dockerfile'dan image build edilirken bir tag'e sahip olması istenirse -t parametresi kullanılabilir.
15 - docker tag image_id tag_name:tag_version --> Belirtilen image_id'ye sahip olan image'nın belirtlen tag ismine ve versiyonuna sahip olmasını sağlar.
16 - docker login --> Komutunu çalıştırdıktan sonra girilen kimlik bilgileri ile Dockerhub'a erişim sağlanır.
17 - docker push image_name --> Belirtilen image_name'e sahip Imageyi Dockerhub'a gönderir.
18 - docker logs container_id --> detached modda çalıştırılan yani çıktıları console attach edilmeyen conttainerlerin loglarını izlemeye yarar.

##DOCKER COMPOSE CHEAT SHEET##
1 - docker-compose build veya docker-compose build service_name --> İlgili service'i build eder.
2 - docker-compose up --> docker-compose.yml içerisindeki tüm servisleri teker teker ayağa kaldırır.--no-recreate veya --force-recreate parametreleri ile kullanılabilir.
--no-recreate parametresi ilgili servislerin yeniden ayağa kalkarken build edilmesini engeller,--force-recreate ise her seferinde servis ayağa kaldırılırken build edilmesini zorunlu kılar.
3 - docker-compose ps --> docker-compose tarafından çalıştırılan servisleri listeler.
4 - docker-compose down --> docker-compose tarafından çalıştırılan servisleri siler.
5 - docker-compose run --> docker-compose.yml dosyası içerisinde belirtilen bir servis ile belirtilen diğer bir servis arasında komutsal işlemleri gerçekleştirir.docker-compose dosyada belirtilen her bir servisin 
birbirileriyle servis isimleri üzerinde haberleşmelerini sağlamak üzere tüm networking ayarlarını yapar.
6 - docker-compose start --> docker-compose.yml içerisinde belirtilen servislerin bir veya bir kaçını başlatmaya yarar aynı işi docker-compose up service_name ile de yapılabilir.
7 - docker-compose stop --> docker-compose.yml içerisinde belirtilen servislerin bir veya bir kaçını durdurmaya yarar.
8 - docker-compose exec --> Çalışan bir servis içerisinde işlem yapabilmeyi sağlar.