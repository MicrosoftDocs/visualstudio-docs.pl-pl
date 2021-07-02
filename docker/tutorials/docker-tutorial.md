---
title: 'Samouczek: wprowadzenie do platformy Docker & Visual Studio Code'
description: Wieloetapowy samouczek, który obejmuje podstawowe informacje dotyczące pracy z platformą Docker przy użyciu Visual Studio Code.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: tutorial
ms.workload:
- azure
next_page: app.md
ms.openlocfilehash: 75a51f478e4e58700f6025dd6a87fcc38439ed87
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222659"
---
# <a name="tutorial-get-started-with-docker"></a>Samouczek: wprowadzenie do platformy Docker

Z tego samouczka dowiesz się więcej na temat tworzenia i wdrażania aplikacji platformy Docker, w tym używania wielu kontenerów z bazą danych i używania Docker Compose. Wdrożysz również konteneryzowana aplikację na platformie Azure.

## <a name="start-the-tutorial"></a>Uruchom samouczek

Jeśli polecenie zostało już uruchomione, aby rozpocząć pracę z samouczkiem, gratulujemy!  Jeśli nie, otwórz wiersz polecenia lub okno powłoki bash i uruchom polecenie:

```cli
docker run -d -p 80:80 docker/getting-started
```

Zauważysz, że jest używanych kilka flag. Poniżej znajdziesz więcej informacji na ich temat:

- `-d` — uruchamianie kontenera w trybie odłączanym (w tle)
- `-p 80:80` — zamapuj port 80 hosta na port 80 w kontenerze
- `docker/getting-started` — obraz do użycia

> [!TIP]
> Możesz połączyć flagi pojedynczego znaku, aby skrócić pełne polecenie.
> Na przykład powyższe polecenie może być zapisane w następujący sposób:
>
> ```cli
> docker run -dp 80:80 docker/getting-started
> ```

## <a name="the-vs-code-extension"></a>Rozszerzenie VS Code

Przed zbyt daleko chcemy wyróżnić rozszerzenie docker VS Code, które zapewnia szybki widok kontenerów uruchomionych na maszynie. Zapewnia szybki dostęp do dzienników kontenerów, umożliwia uzyskanie powłoki wewnątrz kontenera i umożliwia łatwe zarządzanie cyklem życia kontenera (zatrzymywanie, usuwanie itd.).

Aby uzyskać dostęp do rozszerzenia, postępuj zgodnie z instrukcjami [podanymi tutaj.](https://code.visualstudio.com/docs/containers/overview) Użyj ikony platformy Docker po lewej stronie, aby otworzyć widok platformy Docker. Jeśli teraz otworzysz rozszerzenie, ten samouczek zostanie uruchomiony. Nazwa kontenera `angry_taussig` (poniżej) jest losowo utworzoną nazwą. Dlatego najprawdopodobniej będziesz mieć inną nazwę.

![Kontener samouczka uruchomiony w rozszerzeniu platformy Docker](media/vs-tutorial-in-extension.png)

## <a name="what-is-a-container"></a>Co to jest kontener

Co to jest kontener po  uruchomieniu kontenera? Mówiąc prościej, kontener jest po prostu innym procesem na maszynie, który został odizolowany od wszystkich innych procesów na maszynie hosta. Ta izolacja wykorzystuje przestrzenie nazw jądra i [cgroups](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504), funkcje, które były w systemie Linux od dłuższego czasu. Docker pracowała nad tym, aby te możliwości były łatwe w użyciu i łatwe w użyciu.

> [!NOTE]
> **Tworzenie kontenerów od podstaw** Jeśli chcesz zobaczyć, w jaki sposób kontenery są budowane od podstaw, Liz Aki z firmy Aqua Security ma film wideo, w którym tworzy kontener od podstaw w go:
>
> [!VIDEO https://www.youtube-nocookie.com/embed/8fi7uSYlOdc]

## <a name="what-is-a-container-image"></a>Co to jest obraz kontenera

Podczas uruchamiania kontenera jest używany izolowany system plików. Ten niestandardowy system plików jest dostarczany przez **obraz kontenera**. Ponieważ obraz zawiera system plików kontenera, musi zawierać wszystkie elementy potrzebne do uruchomienia aplikacji — wszystkie zależności, konfigurację, skrypty, pliki binarne i tak dalej. Obraz zawiera również inne konfiguracje kontenera, takie jak zmienne środowiskowe, domyślne polecenie do uruchomienia i inne metadane.

W dalszej części dowiemy się więcej na temat obrazów, na przykład warstw, najlepszych rozwiązań i innych.

> [!NOTE]
> Jeśli znasz już kontener , pomyśl `chroot` o kontenerze jako o rozszerzonej wersji programu `chroot` . System plików pochodzi po prostu z obrazu. Jednak kontener dodaje dodatkową izolację, która nie jest dostępna w przypadku korzystania z chroot.

## <a name="next-steps"></a>Następne kroki

Kontynuuj pracę z samouczkiem!

> [!div class="nextstepaction"]
> [Aplikacja](your-application.md)
