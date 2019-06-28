---
title: Test jednostkowy aplikacji konteneryzowanych
author: ghogen
description: Uruchamianie testów jednostkowych przy każdej kompilacji dla projektu platformy Docker w programie Visual Studio
ms.author: ghogen
ms.date: 06/17/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: ec5aea44362cf82f6745671cc0706f80e01a60ad
ms.sourcegitcommit: 0cd282a7584b9bfd4df7882f8fdf3ad8a270e219
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67467411"
---
# <a name="how-to-run-unit-tests-for-a-containerized-app"></a>Instrukcje: Uruchamianie testów jednostkowych dla aplikacji konteneryzowanych

Z każdą kompilacją konteneryzowanych projektu może uruchomić testy jednostkowe, modyfikując z pliku Dockerfile.

## <a name="prerequisites"></a>Wymagania wstępne

- [Pulpitu platformy docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- Zainstaluj [Visual Studio 2019 r.](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)
- Testy jednostkowe, skonfigurować do uruchamiania przy użyciu [polecenia dotnet test](/dotnet/core/tools/dotnet-test)
- Zainstaluj [rozszerzenia okna kontenerów](https://aka.ms/vscontainerspreview)

## <a name="add-unit-tests-to-the-dockerfile"></a>Dodawanie testów jednostkowych do pliku Dockerfile

Program Visual Studio niektóre optymalizacje wydajności specjalne, przed zmodyfikowaniem pliku Dockerfile. Podczas kompilowania **debugowania** konfigurację, Visual Studio kompiluje projekty na komputerze lokalnym i kopiuje wyniki do kontenera. Tak, jest wykonywany tylko pierwszy etap wieloetapowych pliku Dockerfile jak określono w pliku Dockerfile. Aby uzyskać więcej informacji, zobacz [procesu kompilacji narzędzia kontenerów programu Visual Studio](container-build.md).

Aby dodać testy jednostkowe do wieloetapowych pliku Dockerfile `unit-test` etapu do pliku Dockerfile między `build` i `publish` etapów.

```
FROM build AS unit-test
RUN dotnet unit-test --logger:trx
```

Visual Studio uruchamia tylko pierwszy etap **debugowania** konfiguracji, więc `unit-test` etapu tylko jest uruchamiane w **wersji** konfiguracji. Ale nawet w **wersji** konfiguracji, dziennika wyniki nie będą uwzględniane w obrazie końcowym, ponieważ obraz końcowy został opracowany z `base` etapu, nie z `unit-test` etapu. Aby uruchomić testy i utworzenia obrazu, w którym można przeglądać dzienniki, użyj następującego polecenia:

```cmd
docker build --target:unit-test
```

## <a name="next-steps"></a>Następne kroki

Następnie można użyć [okno Kontejneru](view-and-diagnose-containers.md) (Jeśli masz zainstalowane rozszerzenie), aby wyświetlać dzienniki.  

Aby wyświetlić dzienniki testów, użyj **Ctrl**+**Q** i wyszukaj **kontenery** otworzyć **kontenery** okna. W **kontenery** oknie Znajdź kontenera, otwórz **pliki** kartę, poszukaj w systemie plików kontenera pliku wyników testu (.trx) i otwórz go, aby wyświetlić wyniki w programie Visual Studio.

