---
title: Aktualizowanie programu Visual Studio w obrębie punktu odniesienia obsługi
description: Dowiedz się, jak aktualizować Visual Studio pozostając na planie bazowym obsługi.
ms.date: 07/17/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: '>=vs-2019'
ms.openlocfilehash: 03a192657a46c2db15cb2d1121735905f06da478
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306673"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Aktualizowanie programu Visual Studio w obrębie punktu odniesienia obsługi

Często aktualizujemy Visual Studio cyklu życia produktu. Istnieją dwa typy aktualizacji:

* **Drobne aktualizacje wersji** &mdash; na przykład w wersjach od 16.0 do 16.1, &mdash; które zawierają nowe funkcje i składniki.  
* **Aktualizacje obsługi**— na przykład z 16.0.4 do 16.0.5 — które zawierają tylko ukierunkowane poprawki dla krytycznych problemów.

Administratorzy przedsiębiorstwa mogą zdecydować się na utrzymanie klientów w planie bazowym obsługi. Plan bazowy obsługi jest obsługiwany za pomocą aktualizacji obsługi z roku po wydaniu następnego planu bazowego obsługi.

Opcja planu bazowego obsługi zapewnia deweloperom i administratorom większą elastyczność w zakresie przyjmowania nowych funkcji, poprawek błędów lub składników zawartych w nowych drobnych aktualizacjach. Pierwszy plan bazowy obsługi to 16.0.x. Aby uzyskać więcej informacji, zobacz [Opcje pomocy technicznej dla klientów korporacyjnych i profesjonalnych.](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers)

## <a name="how-to-get-onto-a-servicing-baseline"></a>Jak uzyskać dostęp do planu bazowego obsługi

Aby rozpocząć korzystanie z planu bazowego obsługi, pobierz program inicjujący Visual Studio o stałej wersji ze [strony My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). Program inicjujący zawiera linki do konfiguracji produktu, obciążeń i składników dla określonej wersji.

> [!NOTE]
> Należy zachować ostrożność podczas rozróżniania między programem inicjjącym o stałej wersji a standardowymi programami inicjujący. Program inicjujący w standardowych wersjach jest skonfigurowany do używania najnowszej dostępnej wersji programu Visual Studio. Standardowe boostrappers mają liczbę w nazwie pliku (na przykład vs_enterprise__123456789-123456789.exe), gdy są pobierane z My.VisualStudio.com.

Podczas instalacji administratorzy przedsiębiorstwa muszą skonfigurować swoich klientów, aby uniemożliwić ich aktualizowanie do najnowszej wersji. Istnieje kilka sposobów, aby to zrobić:
- [Zmień ustawienie `channelUri` w pliku konfiguracji odpowiedzi,](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network) aby użyć manifestu kanału w układzie lub folderze lokalnym.
- [Zmodyfikuj channelUri za pomocą wykonywania wiersza polecenia,](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet) aby użyć nieistniejącego pliku.
- [Ustaw zasady w systemie klienta, aby wyłączyć aktualizacje](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating), aby uniemożliwić klientom samodzielne aktualizowanie.

### <a name="install-a-servicing-baseline-on-a-network"></a>Instalowanie planu bazowego obsługi w sieci

Administratorzy, którzy korzystają z instalacji układu sieciowego, powinni zmodyfikować wartość w plikuresponse.jsw układzie, aby używaćchannelmanifest.jsw pliku, który znajduje się w tym `channelUri` samym folderze.   Aby uzyskać instrukcje do podjęcia, zobacz [Control updates to network-based Visual Studio deployments](controlling-updates-to-visual-studio-deployments.md)(Kontrolowanie aktualizacji sieciowych wdrożeń Visual Studio sieciowych). Zmiana wartości `channelUri` umożliwia klientom wyszukiwania aktualizacji w lokalizacji układu.

### <a name="install-a-servicing-baseline-via-the-internet"></a>Instalowanie planu bazowego obsługi za pośrednictwem Internetu

W przypadku instalacji internetowej dodaj element z nieistniejący manifestem kanału do wiersza polecenia używanego `--channelUri` do uruchamiania instalatora. Spowoduje to Visual Studio używania najnowszej dostępnej wersji aktualizacji. Oto przykład:

```shell
vs_enterprise.exe --channelUri c:\doesnotexist.chman
```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>Używanie ustawień zasad w celu wyłączenia aktualizowania klientów

Inną opcją kontrolowania aktualizacji na kliencie jest wyłączenie [powiadomień o aktualizacjach.](controlling-updates-to-visual-studio-deployments.md) Użyj tej opcji, jeśli wartość channelUri nie została zmieniona podczas instalacji. Spowoduje to wyłączenie klienta z otrzymywania linków do najnowszej dostępnej wersji. Program inicjujący o stałej wersji jest nadal niezbędny do zaktualizowania do określonej wersji na kliencie.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Jak utrzymać plan bazowy obsługi

Gdy jest dostępna aktualizacja planu bazowego obsługi, pliki programu inicjjącego w stałej wersji są udostępniane do aktualizacji obsługi na [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0).

W przypadku administratorów wdrażanych przy użyciu instalacji układu sieciowego administrator powinien zaktualizować [lokalizację układu](update-a-network-installation-of-visual-studio.md). Klienci zainstalowani z lokalizacji otrzymają powiadomienia o aktualizacji. Jeśli aktualizacja musi zostać wdrożona na klientach, postępuj zgodnie [z tymi instrukcjami.](update-a-network-installation-of-visual-studio.md#deploy-an-update-to-client-machines) Podczas modyfikowania ustawienia "response.jsna" dla aktualizacji nie należy dodawać dodatkowych obciążeń, składników ani języków. Zarządzanie tymi ustawieniami musi odbywać się jako wdrożenie "modyfikuj" po zaktualizowaniu produktu.

W przypadku instalacji internetowej uruchom nowy program inicjujący o stałej wersji z parametrem, który prowadzi do `--channelUri` nieistniejącego manifestu kanału na kliencie. Jeśli aktualizacja jest wdrażana w trybie cichym lub pasywnym, użyj dwóch oddzielnych poleceń:

1. Zaktualizuj Visual Studio instalatora:

    ```shell
    vs_enterprise.exe --quiet --update
    ```

::: moniker range="vs-2019"
 
2. Zaktualizuj samą Visual Studio aplikacji:
    ```shell
    vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

::: moniker-end

::: moniker range=">=vs-2022"

2. Zaktualizuj samą Visual Studio aplikacji:
    ```shell
    vs_enterprise.exe update --installPath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](tools-for-managing-visual-studio-instances.md)
* [Jak zdefiniować ustawienia w pliku odpowiedzi](automated-installation-with-response-file.md)
* [Kontrolowanie aktualizacji wdrożeń Visual Studio sieciowych](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio produktu i jego obsługa](/visualstudio/releases/2019/servicing/)
