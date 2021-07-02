---
title: 'Samouczek platformy Docker — część 5: korzystanie z instalacji powiązania'
description: Opisuje sposób używania instalacji powiązania do kontrolowania punktu instalacji na hoście.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: ad3737ccfa4b0dae8ad427bd79e4adeb2756795b
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222763"
---
# <a name="use-bind-mounts"></a>Korzystanie z instalacji powiązynych

W poprzednim rozdziale o tym,  jak używać nazwanego woluminu do utrwalania danych w bazie danych, dowiedzieliśmy się więcej. Nazwane woluminy są doskonałe, jeśli chcesz po prostu przechowywać dane, ponieważ nie musisz martwić się o miejsce przechowywania danych. 

W **przypadku instalacji powiązania** można kontrolować dokładny punkt instalacji na hoście. Można jej użyć do utrwalania danych, ale jest ona często używana do zapewnienia dodatkowych danych w kontenerach. Podczas pracy nad aplikacją możesz użyć instalacji powiązania, aby zainstalować kod źródłowy w kontenerze, aby zobaczyć zmiany kodu, odpowiedzieć i od razu zobaczyć zmiany.

W przypadku aplikacji opartych na węzłach [narzędzie nodemon](https://npmjs.com/package/nodemon) jest doskonałym narzędziem do obserwowania zmian plików, a następnie ponownego uruchamiania aplikacji. W większości innych języków i platform istnieją równoważne narzędzia.

## <a name="quick-volume-type-comparisons"></a>Szybkie porównania typów woluminów

Dwoma głównymi typami woluminów, które są dostępne z aparatem platformy Docker, są instalacji powiązania i nazwanych woluminów. Dostępne są jednak dodatkowe sterowniki woluminów do obsługi innych przypadków użycia[(SFTP,](https://github.com/vieux/docker-volume-sshfs) [Ceph,](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/) [NetApp,](https://netappdvp.readthedocs.io/en/stable/) [S3](https://github.com/elementar/docker-s3-volume)i innych).

| Właściwość | Nazwane woluminy | Powiązywaj instalacji |
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

    - `-dp 3000:3000` — tak jak poprzednio. Uruchamianie w trybie odłączony (w tle) i tworzenie mapowania portów
    - `-w /app` — ustawia "katalog roboczy" lub bieżący katalog, z których zostanie uruchomione polecenie
    - `-v "%cd%:/app"` - Powiąż zainstaluj bieżący katalog z hosta w kontenerze do `/app` katalogu
    - `node:12-alpine` — obraz do użycia. Należy pamiętać, że jest to obraz podstawowy aplikacji z pliku Dockerfile
    - `sh -c "yarn install && yarn run dev"` — polecenie . Uruchamiamy powłokę przy użyciu narzędzia (alpine nie ma ) i uruchamiamy program , aby zainstalować wszystkie zależności, a `sh` `bash` następnie `yarn install` uruchamiać  . `yarn run dev` Jeśli popatrzysz w `package.json` skrypcie , zobaczysz, że skrypt uruchamia `dev` . `nodemon`

1. Dzienniki można obserwować przy użyciu narzędzia `docker logs -f <container-id>` . Gdy zobaczysz, że wszystko jest gotowe do pracy:

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

    Po obejrzeniu dzienników zakończ działanie, naciskając klawisz `Ctrl` + `C` .

1. Teraz zmień aplikację. W pliku `src/static/js/app.js` zmień przycisk Add Item **(Dodaj element),** aby po prostu powiedzieć **Add (Dodaj).** Ta zmiana zostanie w wierszu 109.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. Wystarczy odświeżyć stronę (lub otworzyć ją), aby zmiany powinny zostać odzwierciedlone w przeglądarce niemal natychmiast. Ponowne uruchomienie serwera Node może potrwać kilka sekund, więc jeśli wystąpi błąd, po prostu spróbuj odświeżyć po kilku sekundach.

    ![Zrzut ekranu przedstawiający zaktualizowaną etykietę przycisku Dodaj](media/updated-add-button.png)

1. Możesz wprowadzić inne zmiany, które chcesz wprowadzić. Gdy wszystko będzie gotowe, zatrzymaj kontener i skompilowaj nowy obraz przy `docker build -t getting-started .` użyciu .

Korzystanie z instalacji powiązywu *jest bardzo* typowe w przypadku lokalnych konfiguracji programistów. Zaletą jest to, że maszyna dewelopera nie musi mieć zainstalowanych wszystkich narzędzi do kompilacji i środowisk. Za pomocą jednego `docker run` polecenia środowisko dewelopera jest ściągane i gotowe do użycia. Więcej informacji na temat Docker Compose w przyszłym kroku, ponieważ pomoże to uprościć polecenia (masz już wiele flag).

## <a name="recap"></a>Podsumowanie

W tym momencie możesz utrwalić bazę danych i szybko reagować na potrzeby i potrzeby swoich inwestorów i twórców. Brawo! Ale zgadnij, co? Otrzymano wspaniałe wiadomości!

**Twój projekt został wybrany do przyszłego rozwoju.**

Aby przygotować się do produkcji, musisz zmigrować bazę danych z pracy w sqlite do czegoś, co może nieco lepiej skalować. Dla uproszczenia będziesz korzystać z relacyjnej bazy danych i przełączysz aplikację na korzystanie z programu MySQL. Ale jak należy uruchomić mysql? Jak zezwolić kontenerom na rozmowę ze sobą? Dowiesz się o tym w następnej.

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem!

> [!div class="nextstepaction"]
> [Aplikacje z wieloma kontenerami](multi-container-apps.md)