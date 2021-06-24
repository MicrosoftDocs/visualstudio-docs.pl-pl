---
title: 'Samouczek platformy Docker — część 5: korzystanie z instalacji powiązania'
description: Opisuje sposób używania instalacji powiązania do kontrolowania punktu instalacji na hoście.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 6a4aa7623f69f9b02f9649a1a66ade010a823669
ms.sourcegitcommit: 98d187abd9352d2255348b84d99d015e65caa0ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2021
ms.locfileid: "112574116"
---
# <a name="use-bind-mounts"></a>Korzystanie z instalacji powiązania

W poprzednim rozdziale dowiedzieliśmy się  więcej o nazwanych woluminach i utrwaliliśmy je w bazie danych. Nazwane woluminy są doskonałe, jeśli chcesz po prostu przechowywać dane, ponieważ nie musisz martwić się o miejsce przechowywania danych. 

W **przypadku instalacji powiązania** można kontrolować dokładny punkt instalacji na hoście. Można jej użyć do utrwalania danych, ale jest ona często używana do zapewnienia dodatkowych danych w kontenerach. Podczas pracy nad aplikacją można użyć instalacji powiązania, aby zainstalować kod źródłowy w kontenerze, aby zobaczyć zmiany kodu, odpowiedzieć i od razu zobaczyć zmiany.

W przypadku aplikacji opartych na węzłach [narzędzie nodemon](https://npmjs.com/package/nodemon) jest doskonałym narzędziem do obserwowania zmian plików, a następnie ponownego uruchamiania aplikacji. W większości innych języków i platform istnieją równoważne narzędzia.

## <a name="quick-volume-type-comparisons"></a>Szybkie porównania typów woluminów

Zainstaluje powiązania i nazwane woluminy to dwa główne typy woluminów, które są dostępne z aparatem platformy Docker. Dostępne są jednak dodatkowe sterowniki woluminów do obsługi innych przypadków użycia[(SFTP,](https://github.com/vieux/docker-volume-sshfs) [Ceph,](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/) [NetApp,](https://netappdvp.readthedocs.io/en/stable/) [S3](https://github.com/elementar/docker-s3-volume)i innych).

| Właściwość | Nazwane woluminy | Wiązanie instalacji |
| -------- | ------------- | ----------- |
| Lokalizacja hosta | Docker wybiera | Kontrolujesz |
| Przykład instalacji (przy użyciu `-v` ) | my-volume:/usr/local/data | /path/to/data:/usr/local/data |
| Wypełnia nowy wolumin zawartością kontenera | Tak | Nie |
| Obsługuje sterowniki woluminów | Tak | Nie |

## <a name="start-a-dev-mode-container"></a>Uruchamianie kontenera w trybie dewelopera

Aby uruchomić kontener w celu obsługi przepływu pracy projektowania, należy wykonać następujące czynności:

- Zainstaluj kod źródłowy w kontenerze
- Zainstaluj wszystkie zależności, w tym zależności "dewelopera"
- Uruchom nodemon, aby obserwować zmiany systemu plików

1. Upewnij się, że nie masz uruchomionych żadnych `getting-started` poprzednich kontenerów.

1. Uruchom następujące polecenie (zastąp znaki ` \ ` znakiem `` ` `` w Windows PowerShell). Później dowiesz się, co się dzieje:

    ```bash
    docker run -dp 3000:3000 \
        -w /app \
        -v "%cd%:/app" \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000` — tak samo jak wcześniej. Uruchamianie w trybie odłączony (w tle) i tworzenie mapowania portów
    - `-w /app` — ustawia "katalog roboczy" lub bieżący katalog, z których zostanie uruchomione polecenie
    - `-v "%cd%:/app"` — powiąż z katalogiem zainstaluj bieżący katalog z hosta w `/app` kontenerze
    - `node:12-alpine` — obraz do użycia. Należy pamiętać, że jest to obraz podstawowy aplikacji z pliku Dockerfile
    - `sh -c "yarn install && yarn run dev"` — polecenie . Uruchamiamy powłokę przy użyciu narzędzia (alpine nie ma ) i uruchamiamy program , aby zainstalować wszystkie zależności, a `sh` następnie `bash` `yarn install` uruchamiać .  `yarn run dev` Jeśli popatrzysz na `package.json` , zobaczymy, że `dev` skrypt uruchamia . `nodemon`

1. Dzienniki można obserwować przy użyciu narzędzia `docker logs -f <container-id>` . Gdy zobaczysz, że wszystko jest gotowe:

    ```bash
    docker logs -f <container-id>
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Using sqlite database at /etc/todos/todo.db
    Listening on port 3000
    ```

    Gdy wszystko będzie gotowe do obserwowania dzienników, zamknij, naciskając klawisz `Ctrl` + `C` .

1. Teraz zmień aplikację. W pliku `src/static/js/app.js` zmień przycisk Dodaj **element,** aby po prostu powiedzieć **Dodaj**. Ta zmiana będzie w wierszu 109.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. Wystarczy odświeżyć stronę (lub otworzyć ją). Zmiana powinna zostać natychmiast odzwierciedlona w przeglądarce. Ponowne uruchomienie serwera Node może potrwać kilka sekund, więc jeśli wystąpi błąd, po prostu spróbuj odświeżyć po kilku sekundach.

    ![Zrzut ekranu przedstawiający zaktualizowaną etykietę przycisku Dodaj](media/updated-add-button.png)

1. Możesz wprowadzić inne zmiany, które chcesz wprowadzić. Gdy wszystko będzie gotowe, zatrzymaj kontener i skompilowaj nowy obraz przy użyciu funkcji `docker build -t getting-started .` .

Korzystanie z instalacji powiązywu *jest bardzo* typowe w przypadku lokalnych konfiguracji programistów. Zaletą jest to, że maszyna dewelopera nie musi mieć zainstalowanych wszystkich narzędzi do kompilacji i środowisk. Za pomocą jednego `docker run` polecenia środowisko dewelopera jest ściągane i gotowe do użycia. Dowiesz się więcej o Docker Compose w przyszłym kroku, ponieważ pomoże to uprościć polecenia (masz już wiele flag).

## <a name="recap"></a>Podsumowanie

W tym momencie możesz utrwalić bazę danych i szybko reagować na potrzeby i wymagania swoich inwestycji i twórców. Brawo! Ale co zgadnąć? Otrzymano wspaniałe wiadomości!

**Twój projekt został wybrany do przyszłego tworzenia!**

Aby przygotować się do produkcji, musisz zmigrować bazę danych z pracy w sqlite do czegoś, co może nieco lepiej skalować. Dla uproszczenia będziesz korzystać z relacyjnej bazy danych i przełączysz aplikację do korzystania z programu MySQL. Ale jak należy uruchomić mysql? Jak zezwolić kontenerom na rozmowę ze sobą? Dowiesz się o tym w następnej.

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem!

> [!div class="nextstepaction"]
> [Aplikacje z wieloma kontenerami](multi-container-apps.md)