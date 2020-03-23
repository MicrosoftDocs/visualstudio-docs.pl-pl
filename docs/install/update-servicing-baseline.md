---
title: Aktualizowanie programu Visual Studio w obrębie punktu odniesienia obsługi
description: Dowiedz się, jak zaktualizować program Visual Studio podczas pozostawania w linii bazowej obsługi.
ms.date: 07/17/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9f31a3f7ae5e0e0ca4150d88870b9e48493bffcc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114957"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Aktualizowanie programu Visual Studio w obrębie punktu odniesienia obsługi

Możemy aktualizować Visual Studio często w cyklu życia produktu. Istnieją dwa typy aktualizacji: 

* **Drobne aktualizacje**&mdash;wersji, na przykład, 16.0&mdash;do 16.1, które zawierają nowe funkcje i składniki.  
* **Obsługa aktualizacji**— na przykład od 16.0.4 do 16.0.5 — które zawierają tylko ukierunkowane poprawki w przypadku problemów krytycznych.

Administratorzy przedsiębiorstwa mogą zachować swoich klientów w linii bazowej obsługi. Linia bazowa obsługi jest obsługiwana z aktualizacjami obsługi przez rok po wydaniu następnej linii bazowej obsługi.

Opcja linii bazowej obsługi daje deweloperom i administratorom większą elastyczność w przyjmowaniu nowych funkcji, poprawek błędów lub składników zawartych w nowych aktualizacjach pomocniczych. Pierwsza linia bazowa obsługi to 16.0.x. Aby uzyskać więcej informacji, zobacz [Opcje pomocy technicznej dla klientów korporacyjnych i profesjonalnych](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers).

## <a name="how-to-get-onto-a-servicing-baseline"></a>Jak dostać się do linii bazowej obsługi

Aby rozpocząć korzystanie z planu bazowego obsługi, pobierz program inicjujący instalatora programu Visual Studio w wersji stałej z [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). Program bootstrappers mają łącza do konfiguracji produktu, obciążeń i składników dla tej konkretnej wersji.

> [!NOTE]
> Należy zachować ostrożność, aby odróżnić bootstrapper wersji stałej i standardowych bootstrappers. Standardowe programy inichowania są skonfigurowane do używania najnowszej dostępnej wersji programu Visual Studio. Standardowe boostrappers mają numer w nazwie pliku (na przykład vs_enterprise__123456789-123456789.exe), gdy są pobierane z My.VisualStudio.com.

Podczas instalacji administratorzy przedsiębiorstwa muszą skonfigurować swoich klientów, aby uniemożliwić klientom aktualizowanie do najnowszej wersji. Istnieje kilka sposobów, aby to zrobić:
- [Zmień `channelUri` ustawienie w pliku konfiguracji odpowiedzi,](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network) aby użyć manifestu kanału w układzie lub folderze lokalnym.
- [Zmodyfikuj channelUri za pomocą wykonywania wiersza polecenia,](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet) aby użyć nieistniejącego pliku.
- [Ustaw zasady w systemie klienckim, aby wyłączyć aktualizacje,](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating)aby uniemożliwić klientom samoaktualnie.

### <a name="install-a-servicing-baseline-on-a-network"></a>Instalowanie planu bazowego obsługi w sieci

Administratorzy korzystający z instalacji `channelUri` układu sieciowego powinni zmodyfikować wartość w pliku *response.json* w układzie, aby użyć pliku *channelmanifest.json* znajdującego się w tym samym folderze. Aby uzyskać kroki do podjęcia, zobacz [Aktualizacje sterowania wdrożeniami programu Visual Studio opartymi na sieci.](controlling-updates-to-visual-studio-deployments.md) Zmiana `channelUri` wartości umożliwia klientom wyszukywać aktualizacje w lokalizacji układu.

### <a name="install-a-servicing-baseline-via-the-internet"></a>Instalowanie linii bazowej obsługi za pośrednictwem Internetu

W przypadku instalacji internetowej `--channelUri` dodaj z nieistniejącym manifestem kanału do wiersza polecenia używanego do uruchamiania konfiguracji. Spowoduje to wyłączenie programu Visual Studio z wykorzystaniem najnowszej dostępnej wersji dla aktualizacji. Oto przykład:

```cmd
vs_enterprise.exe --channelUri c:\doesnotexist.chman
```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>Wyłączanie aktualizacji przez klientów za pomocą ustawień zasad

Inną opcją kontrolowania aktualizacji na kliencie jest [wyłączenie powiadomień o aktualizacji](controlling-updates-to-visual-studio-deployments.md). Użyj tej opcji, jeśli wartość channelUri nie została zmieniona podczas instalacji. Spowoduje to wyłączenie klienta od odbierania łączy do najnowszej dostępnej wersji. Program iniekcji w wersji stałej jest nadal konieczne, aby zaktualizować do określonej wersji na kliencie.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Jak pozostać na linii bazowej obsługi

Gdy dostępna jest aktualizacja linii bazowej obsługi, pliki bootstrapperów o stałej wersji są udostępniane do obsługi aktualizacji w [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0).

W przypadku administratorów, którzy wdrażają przy użyciu instalacji układu sieciowego, administrator powinien zaktualizować [lokalizację układu](update-a-network-installation-of-visual-studio.md). Klienci, którzy zainstalowali z lokalizacji, otrzymają powiadomienia o aktualizacjach. Jeśli aktualizacja musi zostać wdrożona na klientach, postępuj zgodnie z [tymi instrukcjami](update-a-network-installation-of-visual-studio.md#deploy-an-update-to-client-machines). Podczas modyfikowania "response.json" dla aktualizacji, nie należy dodawać dodatkowych obciążeń, składników lub języków. Zarządzanie tymi ustawieniami musi odbywać się jako wdrożenie "modyfikuj" po zaktualizowaniu produktu.

W przypadku instalacji internetowej uruchom nowy program uruchamiający `--channelUri` wersję stałą z parametrem wskazującym nieistniejący manifest kanału na kliencie. Jeśli aktualizacja jest wdrażana w trybie cichym lub pasywnym, użyj dwóch oddzielnych poleceń:

1. Zaktualizuj instalator programu Visual Studio:

    ```cmd
    vs_enterprise.exe --quiet --update
    ```

2. Zaktualizuj samą aplikację programu Visual Studio:

    ```cmd
    vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalacja programu Visual Studio](install-visual-studio.md)
* [Przewodnik dla administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Instalowanie programu Visual Studio za pomocą parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](tools-for-managing-visual-studio-instances.md)
* [Jak zdefiniować ustawienia w pliku odpowiedzi](automated-installation-with-response-file.md)
* [Sterowanie aktualizacjami wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md)
* [Cykl życia produktu i serwis programu Visual Studio](/visualstudio/releases/2019/servicing/)
