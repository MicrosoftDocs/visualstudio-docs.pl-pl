---
title: 'Samouczek platformy Docker — część 4: utrwalanie danych'
description: Dowiedz się, jak utrwalać dane w bazie danych i udostępniać katalogi w kontenerze przez instalowanie woluminu.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: c9408e099caaef097be3fc4eea26cee2b1889e8e
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222906"
---
# <a name="persist-your-data"></a>Utrwalanie danych

Jeśli nie zauważysz tego, lista zadań do zdjęć jest czyszczona za każdym razem, gdy uruchamiasz kontener. Dlaczego tak się ujedna? Przyjrzyjmy się, jak działa kontener.

## <a name="the-containers-filesystem"></a>System plików kontenera

Gdy kontener jest uruchamiany, używa różnych warstw z obrazu dla swojego systemu plików. Każdy kontener otrzymuje również własne "miejsce na pliki tymczasowe" do tworzenia, aktualizowania lub usuwania plików. Wszelkie zmiany nie będą widoczne w innym kontenerze, *nawet* jeśli są one korzystające z tego samego obrazu.

### <a name="see-this-in-practice"></a>Zobacz to w praktyce

Aby zobaczyć, jak to dzieje się w akcji, należy uruchomić dwa kontenery i utworzyć plik w każdym z nich. Zobaczysz, że pliki utworzone w jednym kontenerze nie są dostępne w innym.

1. Uruchom kontener, który utworzy plik o nazwie o losowej liczbie od `ubuntu` `/data.txt` 1 do 10000.

    ```bash
    docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"
    ```

    Jeśli zastanawiasz się nad poleceniem , uruchamiasz powłokę bash i przywołujesz dwa polecenia (dlaczego ma polecenie `&&` ). Pierwsza część wybiera pojedynczą liczbę losową i zapisuje ją w `/data.txt` . Drugie polecenie po prostu obserwuje plik w celu utrzymania działania kontenera.

1. Sprawdź, czy możesz wyświetlić dane wyjściowe przy użyciu funkcji `exec` , aby uzyskać dostęp do kontenera. W tym celu otwórz rozszerzenie VS Code i kliknij opcję **Attach Shell (Dołącz powłokę).** Spowoduje to otwarcie powłoki w kontenerze w `exec` VS Code terminalu.

    ![VS Code interfejs wiersza polecenia w kontenerze ubuntu](media/attach_shell.png)

    Zostanie wyświetlony terminal z uruchomionym powłoką w kontenerze systemu Ubuntu. Uruchom następujące polecenie, aby wyświetlić zawartość `/data.txt` pliku. Zamknij ten terminal ponownie.

    ```bash
    cat /data.txt
    ```

    Jeśli wolisz wiersz polecenia, możesz użyć `docker exec` polecenia , aby to zrobić. Musisz uzyskać identyfikator kontenera (użyj polecenia , aby go pobrać) i pobrać `docker ps` zawartość za pomocą następującego polecenia.

    ```bash
    docker exec <container-id> cat /data.txt
    ```

    Powinna zostać wyświetlony losowa liczba.

1. Teraz uruchom inny kontener (ten sam obraz) i zobaczysz, że `ubuntu` nie masz tego samego pliku.

    ```bash
    docker run -it ubuntu ls /
    ```

    I spójrz! Nie ma tam `data.txt` pliku! Wynika to z tego, że został on zapisany w miejscu na początku tylko dla pierwszego kontenera.

1. Usuń pierwszy kontener za pomocą `docker rm -f` polecenia .

## <a name="container-volumes"></a>Woluminy kontenerów

W poprzednim eksperymencie po raz pierwszy każdy kontener rozpoczyna się od definicji obrazu. Kontenery mogą tworzyć, aktualizować i usuwać pliki, ale te zmiany zostaną utracone, gdy kontener zostanie usunięty, a wszystkie zmiany zostaną odizolowane od tego kontenera. W przypadku woluminów można to wszystko zmienić.

[Woluminy](https://docs.docker.com/storage/volumes/) zapewniają możliwość połączenia określonych ścieżek systemu plików kontenera z maszyną hosta. Jeśli katalog w kontenerze jest zainstalowany, zmiany w tym katalogu są również widoczne na maszynie hosta. Jeśli zainstalujemy ten sam katalog między ponownymi uruchomieniami kontenera, zobaczysz te same pliki.

Istnieją dwa główne typy woluminów. W końcu użyjemy obu tych woluminów, ale zaczniesz od **nazwanych woluminów**.

## <a name="persist-your-todo-data"></a>Utrwalanie danych z todo

Domyślnie aplikacja todo przechowuje swoje dane w bazie danych [SQLite o](https://www.sqlite.org/index.html) wartości `/etc/todos/todo.db` . Jeśli nie znasz programu SQLite, nie martw się! Jest to po prostu relacyjnej bazy danych, w której wszystkie dane są przechowywane w jednym pliku. Chociaż nie jest to najlepsze rozwiązanie w przypadku aplikacji na dużą skalę, działa to w przypadku małych pokazów. Później porozmawiamy o przełączeniu na rzeczywisty aparat bazy danych.

Jeśli baza danych jest pojedynczym plikiem, jeśli można utrwalić ten plik na hoście i udostępnić go do następnego kontenera, powinien być w stanie wybrać miejsce, w którym ostatni plik został pozostawiony. Tworząc wolumin i dołączając go (często nazywany "instalowaniem") do katalogu, w którym są przechowywane dane, można utrwalić dane. Gdy kontener zapisuje plik, jest on utrwalany na `todo.db` hoście w woluminie.

Jak wspomniano, użyjemy nazwanego **woluminu**. Nazwany wolumin można nazwać po prostu zasobnikami danych. Na dysku jest zachowywana lokalizacja fizyczna platformy Docker, a wystarczy zapamiętać nazwę woluminu. Za każdym razem, gdy używasz woluminu, docker upewnia się, że są podane poprawne dane.

1. Utwórz wolumin za pomocą `docker volume create` polecenia .

    ```bash
    docker volume create todo-db
    ```

1. Zatrzymaj ponownie kontener aplikacji z todo w widoku platformy Docker (lub za pomocą funkcji ), ponieważ nadal działa bez `docker rm -f <id>` użycia woluminu trwałego.

1. Uruchom kontener aplikacji z todo, ale dodaj flagę , `-v` aby określić instalacji woluminu. Użyjemy nazwanego woluminu i zainstalujemy go w `/etc/todos` pliku , który przechwyci wszystkie pliki utworzone w ścieżce .

    ```bash
    docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
    ```

1. Po otwarciu kontenera otwórz aplikację i dodaj kilka elementów do listy zadań do odrzuceń.

    ![Elementy dodane do listy zadań do zadań](media/items-added.png)

1. Usuń kontener dla aplikacji z todo. Użyj widoku platformy Docker lub `docker ps` , aby uzyskać identyfikator, a następnie go `docker rm -f <id>` usunąć.

1. Uruchom nowy kontener przy użyciu tego samego polecenia co powyżej.

1. Otwórz aplikację. Elementy powinny być nadal na liście.

1. Usuń kontener, gdy wszystko będzie gotowe do wye zaznaczania listy.

Brawo! Wiesz już, jak utrwalać dane.

> [!TIP]
> Chociaż nazwane woluminy i instalacje powiązania (o których mówimy za chwilę) to dwa główne typy woluminów obsługiwane przez domyślną instalację aparatu platformy Docker, dostępnych jest wiele wtyczek sterowników woluminów do obsługi systemu plików NFS, SFTP, NetApp i innych! Będzie to szczególnie ważne po rozpoczęciu uruchamiania kontenerów na wielu hostach w środowisku klastrowym z Swarm, Kubernetes itp.

## <a name="dive-into-your-volume"></a>Zagłębić się w wolumin

Wiele osób często zadaje pytanie "Gdzie w rzeczywistości dane są przechowywane przez platformę *Docker,* gdy używam nazwanego woluminu?". Jeśli chcesz wiedzieć, możesz użyć `docker volume inspect` polecenia .

```bash
docker volume inspect todo-db
[
    {
        "CreatedAt": "2019-09-26T02:18:36Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/todo-db/_data",
        "Name": "todo-db",
        "Options": {},
        "Scope": "local"
    }
]
```

To `Mountpoint` rzeczywista lokalizacja na dysku, na którym są przechowywane dane. Należy pamiętać, że na większości maszyn musisz mieć dostęp do katalogu głównego, aby uzyskać dostęp do tego katalogu z hosta. Ale w tym miejscu jest!

> [!NOTE]
> **Uzyskiwanie dostępu do danych woluminu bezpośrednio w programie Docker Desktop** Podczas uruchamiania w programie Docker Desktop polecenia platformy Docker są w rzeczywistości uruchomione na małej maszynie wirtualnej. Jeśli chcesz sprawdzić rzeczywistą zawartość katalogu *mountpoint,* musisz najpierw uzyskać dostęp do maszyny wirtualnej. W programie WSL 2 znajduje się on w dystrybucji WSL 2 i jest dostępny za pośrednictwem Eksplorator plików.

## <a name="recap"></a>Podsumowanie

W tym momencie masz działające aplikacje, które mogą przetrwać ponowne uruchomienia! Możesz to pokazać swoim inwestycjom i mieć nadzieję, że uda im się wychwycić Twoją wizję!

Jednak wcześniej widzieliśmy, że ponowne kompilowanie obrazów dla każdej zmiany zajmuje dość dużo czasu. Musi być lepszy sposób na wprowadzanie zmian, prawda? W przypadku instalacji powiązywanych (o czym mówiliśmy wcześniej) istnieje lepszy sposób! Przyjrzyjmy się temu teraz!

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem!

> [!div class="nextstepaction"]
> [Korzystanie z instalacji powiązania](use-bind-mounts.md)
