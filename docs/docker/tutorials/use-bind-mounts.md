---
title: 'Samouczek platformy Docker — część 5: używanie instalacji powiązań'
description: Opisuje sposób używania instalacji powiązań do sterowania punktem instalacji na hoście.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 6474179a0714f2407ac37e724b997139206a91fb
ms.sourcegitcommit: f4d734329c82f2c8005b36af4b2b5516d90e6c63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2020
ms.locfileid: "89039154"
---
# <a name="use-bind-mounts"></a>Używanie instalacji powiązań

W poprzednim rozdziale przedstawiono informacje o **nazwanym woluminie** i użyciu go w celu utrwalenia danych w bazie danych. Nazwane woluminy są doskonałe, jeśli chcesz, aby dane były przechowywane, ponieważ nie musisz martwić się o *miejsce* przechowywania danych.

W przypadku **instalacji z powiązaniem**należy kontrolować dokładne mountpoint na hoście. Można go użyć do utrwalania danych, ale jest często używany do dostarczania dodatkowych danych do kontenerów. Podczas pracy nad aplikacją można użyć instalacji wiązania w celu zainstalowania kodu źródłowego w kontenerze, aby umożliwić mu wyświetlanie zmian kodu, reagowanie i natychmiastowe wyświetlanie zmian.

W przypadku aplikacji opartych na węźle [nodemon](https://npmjs.com/package/nodemon) jest doskonałym narzędziem do śledzenia zmian plików, a następnie ponownego uruchomienia aplikacji. Istnieją równoważne narzędzia w większości innych języków i platform.

## <a name="quick-volume-type-comparisons"></a>Szybkie porównywanie typów woluminów

Instalacje bind i nazwane woluminy to dwa główne typy woluminów, które są dostarczane z aparatem platformy Docker. Dostępne są jednak dodatkowe sterowniki woluminów obsługujące inne przypadki użycia ([SFTP](https://github.com/vieux/docker-volume-sshfs), [ceph](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/), [NetApp](https://netappdvp.readthedocs.io/en/stable/), [S3](https://github.com/elementar/docker-s3-volume)itd.).

| Właściwość | Nazwane woluminy | Zainstaluj powiązania |
| -------- | ------------- | ----------- |
| Lokalizacja hosta | Wybór platformy Docker | Kontrolujesz |
| Przykład instalacji (za pomocą polecenia `-v` ) | My-Volume:/usr/local/data | /path/to/data:/usr/local/data |
| Wypełnia nowy wolumin przy użyciu zawartości kontenera | Tak | Nie |
| Obsługuje sterowniki woluminów | Tak | Nie |

## <a name="start-a-dev-mode-container"></a>Uruchom kontener trybu deweloperskiego

Aby uruchomić kontener do obsługi przepływu pracy deweloperskiej, należy wykonać następujące czynności:

- Instalowanie kodu źródłowego w kontenerze
- Zainstaluj wszystkie zależności, w tym zależności "dev"
- Uruchom nodemon, aby obejrzeć zmiany w systemie plików

1. Upewnij się, że nie masz żadnych wcześniejszych kontenerów, które są `getting-started` uruchomione.

1. Uruchom następujące polecenie (Zastąp ` \ ` znaki znakami `` ` `` w programie Windows PowerShell). Dowiesz się, co się dzieje później:

    ```bash
    docker run -dp 3000:3000 \
        -w /app -v ${PWD}:/app \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000` — tak samo jak wcześniej. Uruchom w odłączonym (tle) trybie i Utwórz mapowanie portów
    - `-w /app` -ustawia "katalog roboczy" lub bieżący katalog, z którego zostanie uruchomione polecenie
    - `-v ${PWD}:/app` -bind Zainstaluj bieżący katalog z hosta w kontenerze w `/app` katalogu
    - `node:12-alpine` — obraz do użycia. Należy zauważyć, że jest to podstawowy obraz aplikacji z pliku dockerfile
    - `sh -c "yarn install && yarn run dev"` — polecenie. Uruchamiamy powłokę przy użyciu `sh` (firma Alpine nie ma `bash` ) i nie działa, `yarn install` Aby zainstalować *wszystkie* zależności, a następnie uruchomić polecenie `yarn run dev` . Jeśli zobaczysz `package.json` , zobaczysz, że `dev` skrypt jest uruchamiany `nodemon` .

1. Dzienniki można obejrzeć przy użyciu `docker logs -f <container-id>` . Zobaczysz, że wszystko jest gotowe do użycia, gdy zobaczysz:

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

    Po zakończeniu oglądania dzienników Zakończ pracę przez naciśnięcie `Ctrl` + `C` .

1. Teraz wprowadź zmiany w aplikacji. W `src/static/js/app.js` pliku Zmień przycisk **Dodaj element** , aby po prostu powiedzieć **dodać**. Ta zmiana będzie w wierszu 109.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. Wystarczy odświeżyć stronę (lub otworzyć ją), a następnie natychmiast zobaczyć zmianę odzwierciedloną w przeglądarce. Ponowne uruchomienie serwera węzła może potrwać kilka sekund, więc jeśli wystąpi błąd, po upływie kilku sekund spróbuj odświeżyć.

    ![Zrzut ekranu przedstawiający zaktualizowaną etykietę przycisku Dodaj](media/updated-add-button.png)

1. Możesz wprowadzić inne zmiany, które chcesz wprowadzić. Gdy skończysz, Zatrzymaj kontener i skompiluj nowy obraz przy użyciu polecenia `docker build -t getting-started .` .

Używanie instalacji BIND jest *bardzo* popularne w przypadku instalacji lokalnych. Zaletą jest to, że komputer deweloperski nie musi mieć zainstalowanych wszystkich narzędzi kompilacji i środowisk. Za pomocą jednego `docker run` polecenia środowisko deweloperskie jest ściągane i gotowe do użycia. Dowiesz się więcej na temat Docker Compose w przyszłości, ponieważ pomoże to uprościć polecenia (masz już wiele flag).

## <a name="recap"></a>Podsumowanie

W tym momencie można zachować bazę danych i szybko reagować na potrzeby i wymagania inwestorów i wykrytych. Hura! Ale dopuszczenie co? Otrzymałeś wspaniałe wiadomości!

**Projekt został wybrany do przyszłego rozwoju.**

Aby przygotować się do produkcji, należy przeprowadzić migrację bazy danych z pracy w oprogramowaniu SQLite do elementu, który może być nieco bardziej skalowalny. Dla uproszczenia będziesz przechowywać relacyjną bazę danych i przełączać aplikację w celu korzystania z programu MySQL. Ale w jaki sposób należy uruchomić program MySQL? Jak można zezwolić kontenerom na wzajemne komunikowanie się? Dowiesz się więcej na ten temat.

## <a name="next-steps"></a>Kolejne kroki

Kontynuuj pracę z samouczkiem.

> [!div class="nextstepaction"]
> [Aplikacje z wieloma kontenerami](multi-container-apps.md)