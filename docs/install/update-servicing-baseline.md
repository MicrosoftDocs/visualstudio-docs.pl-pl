---
title: Aktualizowanie programu Visual Studio w obrębie punktu odniesienia obsługi
description: Dowiedz się, jak aktualizować program Visual Studio przy zachowaniu planu bazowego obsługi.
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
monikerRange: '>=vs-2019'
ms.openlocfilehash: f185451a7f12c3c0b24d74d4a24b40d986ec536f
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184396"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Aktualizowanie programu Visual Studio w obrębie punktu odniesienia obsługi

Program Visual Studio jest często aktualizowany w ramach cyklu życia produktu. Istnieją dwa typy aktualizacji: 

* **Drobne aktualizacje wersji** &mdash; na przykład 16,0 do 16,1 &mdash; , który obejmuje nowe funkcje i składniki.  
* **Obsługa aktualizacji**— na przykład 16.0.4 do 16.0.5 — które obejmują tylko rozwiązania przeznaczone do rozwiązywania problemów krytycznych.

Administratorzy przedsiębiorstwa mogą zdecydować się na utrzymanie klientów w linii bazowej obsługi. Linia bazowa obsługi jest obsługiwana w przypadku aktualizacji z obsługą przez rok poza wersją kolejnej linii bazowej obsługi.

Opcja linia bazowa obsługi zapewnia deweloperom i administratorom większą elastyczność w zakresie wdrażania nowych funkcji, poprawek błędów lub składników uwzględnionych w nowych aktualizacjach pomocniczych. Pierwsza linia bazowa obsługi to 16.0. x. Aby uzyskać więcej informacji, zobacz [Opcje pomocy technicznej dla klientów korporacyjnych i Professional](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers).

## <a name="how-to-get-onto-a-servicing-baseline"></a>Jak uzyskać dostęp do linii bazowej obsługi

Aby zacząć korzystać z linii bazowej obsługi, Pobierz stały program inicjujący Instalatora programu Visual Studio z [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). Program inicjujący ma linki do konfiguracji produktu, obciążeń i składników dla tej konkretnej wersji.

> [!NOTE]
> Należy zachować ostrożność w odróżnieniu od programu inicjującego o stałej wersji i standardowych programów inicjujących. Standardowe programy inicjujące są skonfigurowane do korzystania z najnowszej dostępnej wersji programu Visual Studio. Standardowa boostrappers ma numer w nazwie pliku (na przykład vs_enterprise__123456789 -123456789. exe), gdy są pobierane z usługi My.VisualStudio.com.

Podczas instalacji Administratorzy przedsiębiorstwa muszą skonfigurować swoich klientów, aby uniemożliwić aktualizowanie ich przez klientów do najnowszej wersji. Można to zrobić na kilka sposobów:
- [Zmień `channelUri` ustawienie w pliku konfiguracji odpowiedzi](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network) , aby użyć manifestu kanału w układzie lub folderze lokalnym.
- [Zmodyfikuj identyfikator channeluri za pomocą wykonania wiersza polecenia](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet) , aby użyć nieistniejącego pliku.
- [Ustaw zasady w systemie klienta, aby wyłączyć aktualizacje](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating), aby uniemożliwić klientom samoaktualizacji.

### <a name="install-a-servicing-baseline-on-a-network"></a>Zainstaluj linię bazową obsługi w sieci

Administratorzy, którzy korzystają z instalacji układu sieciowego, powinni zmodyfikować `channelUri` wartość w pliku *Response. JSON* w układzie, aby użyć pliku *channelmanifest. JSON* znajdującego się w tym samym folderze. Aby zapoznać się z krokami do wykonania, zobacz [Kontrola aktualizacji do wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md). Zmiana `channelUri` wartości umożliwia klientom wyszukiwanie aktualizacji w lokalizacji układu.

### <a name="install-a-servicing-baseline-via-the-internet"></a>Zainstaluj linię bazową obsługi za pośrednictwem Internetu

W przypadku instalacji internetowej należy dodać `--channelUri` z nieistniejącego manifestu kanału do wiersza polecenia używanego do uruchamiania Instalatora. Spowoduje to wyłączenie programu Visual Studio z poziomu najnowszej dostępnej wersji dla aktualizacji. Oto przykład:

```cmd
vs_enterprise.exe --channelUri c:\doesnotexist.chman
```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>Korzystanie z ustawień zasad w celu wyłączania aktualizacji klientów

Inna opcja kontrolowania aktualizacji na kliencie polega na wyłączeniu [powiadomień o aktualizacji](controlling-updates-to-visual-studio-deployments.md). Użyj tej opcji, jeśli wartość Identyfikator channeluri nie została zmieniona podczas instalacji. Klient nie będzie mógł odbierać linków do najnowszej dostępnej wersji. Program inicjujący o stałej wersji jest nadal niezbędny do zaktualizowania do określonej wersji na kliencie.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Jak pozostać w punkcie odniesienia obsługi

Gdy dostępna jest aktualizacja linii bazowej obsługi, pliki programu inicjującego z ustalonymi wersjami są udostępniane dla aktualizacji obsługi w witrynie [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0).

W przypadku administratorów, którzy wdrażają program przy użyciu instalacji układu sieciowego, administrator powinien zaktualizować [lokalizację układu](update-a-network-installation-of-visual-studio.md). Klienci instalowani z lokalizacji otrzymają powiadomienia o aktualizacji. Jeśli aktualizacja musi zostać wdrożona na klientach, wykonaj [te instrukcje](update-a-network-installation-of-visual-studio.md#deploy-an-update-to-client-machines). Po zmodyfikowaniu pliku Response. JSON dla aktualizacji nie należy dodawać dodatkowych obciążeń, składników ani języków. Zarządzanie tymi ustawieniami musi odbywać się w ramach wdrożenia "Modify" po aktualizacji produktu.

W przypadku instalacji internetowej Uruchom nowy program inicjujący stałej wersji z `--channelUri` parametrem wskazującym nieistniejący manifest kanału na komputerze klienckim. Jeśli aktualizacja została wdrożona w trybie cichym lub pasywnym, użyj dwóch oddzielnych poleceń:

1. Aktualizowanie Instalatora programu Visual Studio:

    ```cmd
    vs_enterprise.exe --quiet --update
    ```

2. Aktualizowanie samej aplikacji Visual Studio:

    ```cmd
    vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](tools-for-managing-visual-studio-instances.md)
* [Jak zdefiniować ustawienia w pliku odpowiedzi](automated-installation-with-response-file.md)
* [Sterowanie aktualizacjami wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md)
* [Cykl życia produktu Visual Studio i obsługa](/visualstudio/releases/2019/servicing/)
