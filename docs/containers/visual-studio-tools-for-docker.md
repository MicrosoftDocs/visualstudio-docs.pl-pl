---
title: Visual Studio Tools for Docker on Windows
description: Poznawanie narzędzi platformy Docker, dostępnych w programie Visual Studio
author: ghogen
ms.author: ghogen
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 68364384a233defeb69203ed4f3ddc8f122e8bb7
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356296"
---
# <a name="docker-in-visual-studio-on-windows"></a>Aparat docker na platformie programu Visual Studio w Windows

::: moniker range="vs-2017"
Narzędzi dostępnych w programie Visual Studio do programowania z użyciem kontenery są łatwe w użyciu i znacznie ułatwiają kompilowanie, uruchamianie i narzędzia compose zadania. Można również uruchomić i debugować swoje kontenery przy użyciu zwykłego **F5** i **Ctrl**+**F5** kluczy z poziomu programu Visual Studio. Można nawet debugowanie całego rozwiązania, jeśli jego kontenerów są zdefiniowane w tym samym *docker-compose.yml* pliku na poziomie rozwiązania.
::: moniker-end
::: moniker range=">=vs-2019"
Narzędzi dostępnych w programie Visual Studio 2019 r do programowania z użyciem kontenery są łatwe w użyciu i znacznie ułatwiają kompilowanie, uruchamianie i narzędzia compose zadania. Można również uruchomić i debugować swoje kontenery przy użyciu zwykłego **F5** i **Ctrl**+**F5** kluczy z poziomu programu Visual Studio. Można nawet debugowanie całego rozwiązania, jeśli jego kontenerów są zdefiniowane w tym samym *docker-compose.yml* pliku na poziomie rozwiązania.
::: moniker-end

> [!NOTE]
> Ten artykuł dotyczy programu Visual Studio w Windows, a nie programu Visual Studio dla komputerów Mac.

> [!TIP]
> Aby dowiedzieć się więcej o instalowaniu platformy Docker for Windows, zobacz [pulpitu platformy Docker for Windows](https://docs.docker.com/docker-for-windows/).

## <a name="docker-support-in-visual-studio"></a>Obsługę platformy docker w programie Visual Studio

::: moniker range="vs-2017"
Istnieją dwa poziomy obsługę platformy Docker, które można dodać do projektu. W projektach ASP.NET Core, można po prostu dodać *pliku Dockerfile* pliku do projektu, należy włączyć obsługę platformy Docker. Następny poziom to obsługa aranżacji kontenerów, który dodaje *pliku Dockerfile* do projektu (jeśli jeszcze nie istnieje) i *docker-compose.yml* pliku na poziomie rozwiązania. Obsługa aranżacji kontenerów przy użyciu narzędzia Docker Compose jest dodawany domyślnie Visual Studio 2017 w wersji 15.0 wersji 15.7. Obsługa aranżacji kontenerów jest wersje funkcji zgłoszenie zgody na uczestnictwo w programie Visual Studio 2017, należy zachować 15,8 lub nowszej. Wersja należy zachować 15,8 lub nowsza obsługuje narzędzia Docker Compose i Service Fabric.
::: moniker-end
::: moniker range=">=vs-2019"
Istnieją dwa poziomy obsługę platformy Docker, które można dodać do projektu. W projektach ASP.NET Core, można po prostu dodać *pliku Dockerfile* pliku do projektu, należy włączyć obsługę platformy Docker. Następny poziom to obsługa aranżacji kontenerów, który dodaje *pliku Dockerfile* do projektu (jeśli jeszcze nie istnieje) i *docker-compose.yml* pliku na poziomie rozwiązania.  Obsługa aranżacji kontenerów to opcjonalna funkcja w Visual Studio 2019 r, który obsługuje narzędzia Docker Compose, Kubernetes i usługi Service Fabric.
::: moniker-end

**Dodaj > obsługę platformy Docker** i **Dodaj > Obsługa Orkiestratora kontenerów** polecenia znajdują się w menu kliknij prawym przyciskiem myszy (lub menu kontekstowego) węzeł projektu dla projektu platformy ASP.NET Core w  **Eksplorator rozwiązań**, jak pokazano na poniższym zrzucie ekranu:

![Dodaj opcję menu obsługę platformy Docker w programie Visual Studio](./media/visual-studio-tools-for-docker/add-docker-support-menu.png)

### <a name="add-docker-support"></a>Dodaj obsługę platformy Docker

Obsługę platformy Docker można dodać do istniejącego projektu platformy ASP.NET Core, wybierając **Dodaj** > **obsługę platformy Docker** w **Eksploratora rozwiązań**. Można również włączyć obsługę platformy Docker podczas tworzenia projektu, wybierając **włączyć obsługę platformy Docker** w **Nowa aplikacja internetowa ASP.NET Core** okno dialogowe, które jest otwierane po kliknięciu **OK** w **nowy projekt** okno dialogowe, jak pokazano na poniższym zrzucie ekranu.

::: moniker range="vs-2017"
![Włącz obsługę platformy Docker dla nowej aplikacji sieci web platformy ASP.NET Core w programie Visual Studio](./media/visual-studio-tools-for-docker/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Włącz obsługę platformy Docker dla nowej aplikacji sieci web platformy ASP.NET Core w programie Visual Studio](./media/visual-studio-tools-for-docker/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

Podczas dodawania lub Włącz obsługę platformy Docker, program Visual Studio dodaje *pliku Dockerfile* pliku do projektu.

::: moniker range="vs-2017"
> [!NOTE]
> Po włączeniu obsługi narzędzia Docker Compose podczas tworzenia projektu dla projektu platformy ASP.NET (.NET Framework, nie w projekcie platformy .NET Core), jak pokazano na poniższym zrzucie ekranu, dodawany jest również obsługa aranżacji kontenerów.

![Włącz Docker compose obsługę projektu programu ASP.NET](media/visual-studio-tools-for-docker/enable-docker-compose-support.png)
::: moniker-end

### <a name="add-container-orchestration-support"></a>Dodanie obsługi aranżacji kontenerów

Do tworzenia rozwiązania wielu kontenerów, należy dodać Obsługa aranżacji kontenerów do swoich projektów. Dzięki temu można uruchamiać i debugować grupę kontenerów (całe rozwiązanie) w tym samym czasie, jeśli są one definiowane w tym samym *docker-compose.yml* pliku.

Aby dodać obsługę aranżacji kontenerów, kliknij prawym przyciskiem myszy węzeł rozwiązania lub projektu w **Eksploratora rozwiązań**i wybierz polecenie **Dodaj > kontener obsługuje aranżacji**. Następnie wybierz **narzędzia Docker Compose**, **Kubernetes i Helm**, lub **usługi Service Fabric** Zarządzanie kontenerów.

Po dodaniu obsługi aranżacji kontenerów do projektu, zobacz *pliku Dockerfile* dodane do projektu i **narzędzia docker compose** dodawany do rozwiązania w folderze **Eksploratora rozwiązań**, jak pokazano poniżej:

![Pliki docker w Eksploratorze rozwiązań w programie Visual Studio](media/visual-studio-tools-for-docker/docker-support-solution-explorer.png)

Jeśli *docker-compose.yml* już istnieje, program Visual Studio po prostu dodaje wymagane wierszy kodu konfiguracji do niego.

## <a name="configure-docker-tools"></a>Konfigurowanie narzędzi platformy Docker

W menu głównym wybierz **Narzędzia > Opcje**i rozwiń **narzędzia kontenerów > Ustawienia**. Ustawienia narzędzia kontenerów są wyświetlane.

![Visual Studio platformy Docker narzędzia Opcje przedstawiający: Automatycznie Ściągnij wymagane obrazy platformy Docker po załadowaniu projektu, automatycznie uruchom kontenery w tle, automatycznie kill kontenerów na Zamknij rozwiązanie i nie Monituj o ufanie certyfikatu SSL.](./media/visual-studio-tools-for-docker/visual-studio-docker-tools-options.png)

Poniższa tabela może pomóc zdecydować, jak ustawić te opcje.

| Nazwa | Ustawienie domyślne | Dotyczy: | Opis |
| -----|:---------------:|:----------:| ----------- |
| Automatycznie Ściągnij wymagane obrazy platformy Docker po załadowaniu projektu | On | Docker Compose | Aby zwiększyć wydajność podczas ładowania projektów programu Visual Studio rozpocznie operacji ściągania aparatu Docker w tle, tak, aby gdy wszystko będzie gotowe uruchomić kod, obraz, który został już pobrany, lub w trakcie pobierania. Jeśli właśnie trwa ładowanie projektów i przeglądania kodu, możesz Wyłącz tę opcję, aby uniknąć pobierania obrazów kontenerów, które nie są potrzebne. |
| Automatycznie uruchom kontenery w tle | On | Docker Compose | Ponownie do zwiększenia wydajności programu Visual Studio tworzy kontener z instaluje wolumin gotowy do podczas kompilowania i uruchamiania kontenera. Jeśli chcesz kontrolować, po utworzeniu kontenera, wyłącz tę opcję. |
| Automatycznie zabij kontenery rozwiązanie, zamknij | On | Docker Compose | Wyłącz tę opcję, jeśli chcesz kontenerów do rozwiązania w celu będą nadal działać po zamknięcie rozwiązania lub zamknięcia programu Visual Studio. |
| Nie monituj o zaufanie certyfikatowi protokołu SSL | Off | Projekty ASP.NET Core 2.1 | Jeśli certyfikatowi protokołu SSL nie jest zaufany, Visual Studio wyświetli monit o za każdym razem, gdy uruchamiasz projekt, chyba że to pole wyboru jest zaznaczone. |

> [!WARNING]
> Jeśli certyfikatowi protokołu SSL nie jest zaufany, a następnie zaznacz odpowiednie pole, aby pominąć monit, żądań sieci web protokołu HTTPS może przestać działać w czasie wykonywania aplikacji lub usługi. W takim przypadku usuń zaznaczenie pola wyboru **nie Monituj** zaznacz pole wyboru Uruchom projekt i wskazać zaufania w wierszu.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o usługach wdrażania i korzystania z narzędzi programu Visual Studio do pracy z kontenerami, przeczytaj następujące artykuły:

[Debugowanie aplikacji w lokalnym kontenerze Docker](vs-azure-tools-docker-edit-and-refresh.md)

[Wdrażanie kontenera platformy ASP.NET do rejestru kontenerów przy użyciu programu Visual Studio](vs-azure-tools-docker-hosting-web-apps-in-docker.md)
