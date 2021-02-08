---
title: 'Samouczek platformy Docker — część 4: utrwalanie danych'
description: Dowiedz się, jak utrwalać dane w bazie danych i udostępniać katalogi w kontenerze, instalując wolumin.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 9ee4109c888888d2dee36804a178f7db8d41753f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841773"
---
# <a name="persist-your-data"></a>Utrwalanie danych

W przypadku niezauważenia Lista zadań do wykonania jest czyszczona po każdym uruchomieniu kontenera. Dlaczego to jest? Przyszczegółowemy się do sposobu działania kontenera.

## <a name="the-containers-filesystem"></a>System plików kontenera

Gdy działa kontener, wykorzystuje różne warstwy z obrazu dla jego systemu plików. Każdy kontener otrzymuje także własne "miejsce na pliki tymczasowe" do tworzenia, aktualizowania lub usuwania plików. Wszelkie zmiany nie będą widoczne w innym kontenerze, *nawet jeśli* używają tego samego obrazu.

### <a name="see-this-in-practice"></a>Zobacz to w ćwiczenia

Aby zobaczyć to w działaniu, należy uruchomić dwa kontenery i utworzyć plik w każdym z nich. Zobaczysz, że pliki utworzone w jednym kontenerze nie są dostępne w innym.

1. Uruchom `ubuntu` kontener, który utworzy plik o nazwie `/data.txt` z liczbą losową z zakresu od 1 do 10000.

    ```bash
    docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"
    ```

    Jeśli jesteś chcesz wiedzieć o poleceniu, uruchamiasz powłokę bash i wywołujemy dwa polecenia (dlaczego ma to `&&` ). Pierwsza część wybiera pojedynczą liczbę losową i zapisuje ją w `/data.txt` . Drugie polecenie po prostu ogląda plik, aby kontynuować działanie kontenera.

1. Sprawdź, czy dane wyjściowe są widoczne przy użyciu, `exec` Aby przejść do kontenera. Aby to zrobić, Otwórz rozszerzenie VS Code i kliknij opcję **Dołącz powłokę** . Spowoduje to `exec` otwarcie powłoki w kontenerze w ramach terminalu vs Code.

    ![VS Code Otwórz interfejs wiersza polecenia w kontenerze Ubuntu](media/attach_shell.png)

    Zostanie wyświetlony Terminal z uruchomioną powłoką w kontenerze Ubuntu. Uruchom następujące polecenie, aby wyświetlić zawartość `/data.txt` pliku. Zamknij ten terminal ponownie.

    ```bash
    cat /data.txt
    ```

    Jeśli wolisz wiersz polecenia, możesz użyć `docker exec` polecenia, aby to zrobić. Musisz uzyskać identyfikator kontenera (Użyj `docker ps` go, aby go pobrać) i pobrać zawartość za pomocą następującego polecenia.

    ```bash
    docker exec <container-id> cat /data.txt
    ```

    Powinna zostać wyświetlona liczba losowa!

1. Teraz Uruchom inny `ubuntu` kontener (ten sam obraz) i zobaczysz, że nie masz tego samego pliku.

    ```bash
    docker run -it ubuntu ls /
    ```

    I Wyszukaj! Brak pliku. `data.txt` Dzieje się tak, ponieważ został on zapisany w miejscu do tymczasowego tylko dla pierwszego kontenera.

1. Przejdź dalej i usuń pierwszy kontener przy użyciu `docker rm -f` polecenia.

## <a name="container-volumes"></a>Woluminy kontenerów

Po powyższym eksperymentie zobaczysz, że każdy kontener rozpoczyna się od definicji obrazu przy każdym uruchomieniu. Kontenery mogą tworzyć, aktualizować i usuwać pliki, ale te zmiany są tracone po usunięciu kontenera i wszystkie zmiany są odizolowane względem tego kontenera. W przypadku woluminów można zmienić wszystkie te wartości.

[Woluminy](https://docs.docker.com/storage/volumes/) zapewniają możliwość łączenia określonych ścieżek systemu plików kontenera z powrotem z maszyną hosta. Jeśli katalog w kontenerze jest zainstalowany, zmiany w tym katalogu są również widoczne na komputerze-hoście. Jeśli instalujesz ten sam katalog między ponownymi uruchomieniami kontenera, zobaczysz te same pliki.

Istnieją dwa główne typy woluminów. ostatecznie będziesz używać obu tych metod, ale zaczniesz od **nazwanych woluminów**.

## <a name="persist-your-todo-data"></a>Utrwalaj dane do zrobienia

Domyślnie aplikacja do zrobienia przechowuje swoje dane w [bazie danych programu SQLite](https://www.sqlite.org/index.html) pod adresem `/etc/todos/todo.db` . Jeśli nie znasz oprogramowania SQLite, nie martw! Jest to po prostu relacyjna baza danych, w której wszystkie dane są przechowywane w pojedynczym pliku. Chociaż nie jest to najlepsze w przypadku aplikacji o dużej skali, działa w przypadku małych pokazów. Porozmawiamy o przełączeniu tego do rzeczywistego aparatu bazy danych w późniejszym czasie.

W przypadku bazy danych o pojedynczym pliku, jeśli można zachować ten plik na hoście i udostępnić go dla następnego kontenera, powinno być możliwe wybranie miejsca, w którym ostatni z nich pozostawiono. Utworzenie woluminu i dołączenie (często nazywane "instalowaniem") do katalogu, w którym są przechowywane dane, można utrwalać dane. Gdy kontener zapisuje w `todo.db` pliku, zostaje utrwalony na hoście w woluminie.

Jak wspomniano, zamierzasz użyć **nazwanego woluminu**. Należy traktować nazwany wolumin jako po prostu zasobnik danych. Platforma Docker utrzymuje lokalizację fizyczną na dysku i Wystarczy pamiętać o nazwie woluminu. Za każdym razem, gdy korzystasz z woluminu, platforma Docker sprawdzi, czy podano poprawne dane.

1. Utwórz wolumin za pomocą `docker volume create` polecenia.

    ```bash
    docker volume create todo-db
    ```

1. Zatrzymaj ponownie kontener aplikacji do zrobienia w widoku platformy Docker (lub w programie `docker rm -f <id>` ), ponieważ nadal działa bez użycia woluminu trwałego.

1. Uruchom kontener aplikacji do zrobienia, ale Dodaj `-v` flagę, aby określić instalację woluminu. użyjesz nazwanego woluminu i zainstalujesz go w programie `/etc/todos` , co spowoduje przechwycenie wszystkich plików utworzonych w ścieżce.

    ```bash
    docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
    ```

1. Po rozpoczęciu kontenera Otwórz aplikację i Dodaj kilka elementów do listy zadań do wykonania.

    ![Elementy dodane do listy zadań do wykonania](media/items-added.png)

1. Usuń kontener dla aplikacji do zrobienia. Użyj widoku platformy Docker lub, `docker ps` Aby uzyskać identyfikator, a następnie `docker rm -f <id>` go usunąć.

1. Uruchom nowy kontener przy użyciu tego samego polecenia z powyższych.

1. Otwórz aplikację. Twoje elementy powinny być nadal widoczne na liście!

1. Po zakończeniu wyewidencjonowywania listy wybierz kontener.

Hura! Teraz wiesz już, jak utrwalać dane.

> [!TIP]
> Podczas gdy nazwane woluminy i instalacje wiązania (w ciągu minuty) są dwa główne typy woluminów obsługiwane przez domyślną instalację aparatu platformy Docker, dostępnych jest wiele wtyczek sterowników woluminów do obsługi systemu plików NFS, SFTP, NetApp i innych. Będzie to szczególnie ważne po rozpoczęciu uruchamiania kontenerów na wielu hostach w środowisku klastrowanym z Swarm, Kubernetes i tak dalej.

## <a name="dive-into-your-volume"></a>Szczegółowe do woluminu

Duża liczba osób często pyta "gdzie jest platforma Docker, *która przechowuje moje* dane, gdy używam nazwanego woluminu?" Jeśli chcesz wiedzieć, możesz użyć `docker volume inspect` polecenia.

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

`Mountpoint`Jest to rzeczywista lokalizacja na dysku, na którym są przechowywane dane. Należy pamiętać, że na większości maszyn należy mieć dostęp do katalogu głównego, aby uzyskać dostęp do niego z hosta. Ale jest to tam, gdzie jest!

> [!NOTE]
> **Uzyskiwanie dostępu do danych woluminu bezpośrednio na pulpicie platformy Docker** W trakcie działania na pulpicie platformy Docker polecenia platformy Docker są w rzeczywistości uruchamiane wewnątrz małej maszyny wirtualnej na maszynie. Jeśli chcesz wyszukać rzeczywistą zawartość katalogu *mountpoint* , musisz najpierw zacząć korzystać z maszyny wirtualnej. W WSL 2 jest to w WSL 2 dystrybucji i można uzyskać do niego dostęp za pomocą Eksploratora plików.

## <a name="recap"></a>Podsumowanie

W tym momencie masz działającą aplikację, która może przetrwać ponowne uruchomienie. Można je wyświetlić dla inwestorów i mamy nadzieję, że mogą oni przechwycić swoją wizję.

Jednak wcześniej wykorzystano, że ponowne kompilowanie obrazów dla każdej zmiany zajmuje trochę czasu. Aby móc wprowadzać zmiany, należy mieć lepszy sposób? W przypadku instalacji z powiązaniem (które zostały podpowiedź w starszej wersji) istnieje lepszy sposób. Przyjrzyjmy się już teraz!

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem.

> [!div class="nextstepaction"]
> [Używanie instalacji bind](use-bind-mounts.md)
