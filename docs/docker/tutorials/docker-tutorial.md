---
title: Samouczek platformy Docker — wprowadzenie do platformy Docker
description: Wieloetapowy samouczek, który obejmuje podstawowe informacje dotyczące pracy z platformą Docker z Visual Studio Code.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
next_page: app.md
ms.openlocfilehash: 9961810ad408a384db46439235b0b7acab325062
ms.sourcegitcommit: f4d734329c82f2c8005b36af4b2b5516d90e6c63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2020
ms.locfileid: "89039247"
---
# <a name="tutorial-get-started-with-docker"></a>Samouczek: wprowadzenie do platformy Docker

W ramach tego samouczka nauczysz się tworzyć i wdrażać aplikacje platformy Docker, w tym używanie wielu kontenerów z bazą danych, a przy użyciu Docker Compose. Wdrożono również aplikację kontenera na platformie Azure.

## <a name="start-the-tutorial"></a>Uruchom samouczek

Jeśli masz już uruchomione polecenie, aby rozpocząć pracę z samouczkiem, gratulacje!  Jeśli nie, Otwórz wiersz polecenia lub okno bash i uruchom polecenie:

```cli
docker run -d -p 80:80 docker/getting-started
```

Zauważysz, że używane są kilka flag. Oto więcej informacji na ich temat:

- `-d` -Uruchom kontener w trybie odłączonym (w tle)
- `-p 80:80` -Mapuj port 80 hosta na port 80 w kontenerze
- `docker/getting-started` -obraz do użycia

> [!TIP]
> Można połączyć pojedyncze flagi, aby skrócić pełne polecenie.
> Przykładowo powyższe polecenie można napisać jako:
>
> ```cli
> docker run -dp 80:80 docker/getting-started
> ```

## <a name="the-vs-code-extension"></a>Rozszerzenie VS Code

Przed przeprowadzeniem zbyt dużej ilości danych, chcemy wyróżnić rozszerzenie Docker VS Code, które umożliwia szybkie wyświetlenie kontenerów uruchomionych na maszynie. Zapewnia ona szybki dostęp do dzienników kontenerów, umożliwia uzyskanie powłoki wewnątrz kontenera i pozwala łatwo zarządzać cyklem życia kontenera (zatrzymać, usunąć itd.).

Aby uzyskać dostęp do rozszerzenia, postępuj zgodnie z instrukcjami znajdującymi się [tutaj](https://code.visualstudio.com/docs/containers/overview). Użyj ikony Docker po lewej stronie, aby otworzyć widok platformy Docker. Jeśli teraz otworzysz rozszerzenie, zobaczysz, że ten samouczek jest uruchomiony. Nazwa kontenera ( `angry_taussig` poniżej) jest losowo utworzona. Dlatego najprawdopodobniej będziesz mieć inną nazwę.

![Kontener samouczka działający w rozszerzeniu platformy Docker](media/vs-tutorial-in-extension.png)

## <a name="what-is-a-container"></a>Co to jest kontener

Teraz, po uruchomieniu kontenera, co *to jest* kontener? Po prostu kontener jest po prostu innym procesem na komputerze, który został odizolowany od wszystkich innych procesów na komputerze-hoście. Izolacja wykorzystuje [przestrzenie nazw jądra i cgroup](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504), funkcje, które były w systemie Linux przez długi czas. Platforma Docker pracowała nad tym, że funkcje te mogą być łatwo dostępne i łatwe w użyciu.

> [!NOTE]
> **Tworzenie kontenerów od podstaw** Jeśli chcesz zobaczyć, jak kontenery są tworzone od podstaw, ryż Liz z zabezpieczeń akwamaryna ma wideo, w którym tworzy kontener od podstaw:
>
> [!VIDEO https://www.youtube-nocookie.com/embed/8fi7uSYlOdc]

## <a name="what-is-a-container-image"></a>Co to jest obraz kontenera

Podczas uruchamiania kontenera korzysta z wyizolowanego systemu plików. Ten niestandardowy system plików jest dostarczany przez **obraz kontenera**. Ponieważ obraz zawiera system plików kontenera, musi zawierać wszystko, co jest potrzebne do uruchomienia aplikacji — wszystkie zależności, konfiguracja, skrypty, pliki binarne i tak dalej. Obraz zawiera również inne konfiguracje dla kontenera, takie jak zmienne środowiskowe, domyślne polecenie do uruchomienia i inne metadane.

Będziemy szczegółowe bardziej szczegółowe informacje na temat tego, co obejmuje takie jak warstwowe, najlepsze rozwiązania i inne.

> [!NOTE]
> Jeśli znasz już `chroot` program, pomyśl o kontenerze jako rozszerzoną wersję programu `chroot` . System plików jest po prostu pochodzący z obrazu. Jednak kontener dodaje dodatkową izolację niedostępną po prostu przy użyciu chroot.

## <a name="next-steps"></a>Kolejne kroki

Kontynuuj pracę z samouczkiem.

> [!div class="nextstepaction"]
> [Aplikacja](your-application.md)
