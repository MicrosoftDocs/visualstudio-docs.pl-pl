---
title: Aktualizacja programu Visual Studio znajduje się w obsługi punktu odniesienia
titleSuffix: ''
description: Dowiedz się, jak zaktualizować program Visual Studio, pozostając na obsługi linii bazowej.
ms.date: 05/22/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: doughall
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8928feffed77f8bfbb3787bd9a20737b9c7b3f9e
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66213849"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Aktualizacja programu Visual Studio znajduje się w obsługi punktu odniesienia

Visual Studio 2019 będzie miał częste aktualizacje podczas jego [cyklu życia produktu](/visualstudio/productinfo/release-rhythm.md#release-channel-updates). Obejmują one zarówno aktualizacje wersji pomocniczej (na przykład: 16.0 do 16.1) który może zawierać nowe funkcje i składniki i aktualizacje obsługi (na przykład: tylko 16.0.4 do 16.0.5) zawierający docelowe poprawki dotyczące problemów krytycznych. 

Administratorzy przedsiębiorstwa można przechowywać swoich klientów na obsługi linii bazowej, która jest obsługiwane w przypadku obsługi aktualizacji dla roku ostatnie wydanie następnej obsługi linii bazowej. To daje większą elastyczność dla deweloperów i administratorów przyjęcie nowe funkcje, poprawki usterek i składników zawartych w nowe aktualizacje pomocnicze. Pierwszy obsługi punkt odniesienia jest 16.0.x. Zobacz [opcje pomocy technicznej dla subskrypcji enterprise i professional klientów](/visualstudio/releases/2019/servicing.md#support-options-for-enterprise-and-professional-customers) Aby uzyskać więcej informacji.

## <a name="how-to-get-onto-a-servicing-baseline"></a>Jak się dostać się do obsługi punktu odniesienia

Aby rozpocząć korzystanie z obsługi linii bazowej, Pobierz program inicjujący Instalatora programu Visual Studio poprawionej wersji z [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). Tych programów inicjujących zawierają łącza do konfiguracji produktu, obciążeń i składników dla tej określonej wersji. 

> [!NOTE]
> Uważaj rozróżnić program inicjujący poprawionej wersji i normalnym programów inicjujących. Normalne programów inicjujących są skonfigurowane do używania najnowszych dostępnych wersji programu Visual Studio. Mają one liczbą w nazwie pliku (na przykład: vs_enterprise__123456789 123456789.exe), gdy pobrane z my.visualstudio.com.

Podczas instalacji Administratorzy przedsiębiorstwa należy skonfigurować swoich klientów, aby zapobiec ich aktualizowanie do najnowszej wersji. Można to zrobić [zmiana ustawienia identyfikator channelUri w pliku konfiguracyjnym odpowiedzi](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network) do użycia przez manifest kanału w układzie lub lokalny folder [modyfikowanie identyfikator channelUri za pośrednictwem wiersza polecenia wykonywania](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet)przy użyciu pliku nie istnieje, lub [ustawiania zasad w systemie klienta w celu wyłączenia aktualizacji](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating) aby uniemożliwić klientom korzystającym z samoaktualizacji. 

### <a name="install-a-servicing-baseline-on-a-network"></a>Instalowanie obsługi linii bazowej w sieci

Aby zainstalować administratorów przy użyciu układu sieci, zmodyfikuj wartość Identyfikator channelUri w `response.json` w układzie używać channelmanifest.json, który znajduje się w tym samym folderze. Zobacz [kontrolowania aktualizacji z wdrożeniami programu Visual Studio sieciowymi programami wykorzystującymi](controlling-updates-to-visual-studio-deployments.md) wskazówki krok po kroku. Zmiana identyfikator channelUri umożliwia klientom wyszukać aktualizacje w lokalizacji układu. 

### <a name="install-a-servicing-baseline-via-the-internet"></a>Instalowanie obsługi linii bazowej, za pośrednictwem Internetu

Jeśli jest on zainstalowany na podstawie internet, należy dodać `--channelUri` z kanałem nieistniejącej manifestu do wiersza polecenia używane do uruchomienia Instalatora. Powoduje to wyłączenie programu Visual Studio z przy użyciu najnowszej wersji aktualizacji. Oto przykład:

  ```cmd
   vs_enterprise.exe --channelUri c:\doesnotexist.chman 
  ```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>Aby wyłączyć aktualizowanie za pomocą ustawień zasad

Inną opcją w celu kontrolowania aktualizacji na kliencie jest [wyłączyć powiadomienia o aktualizacji](controlling-updates-to-visual-studio-deployments.md). Użyj tej opcji, jeśli identyfikator channelUri wartość nie została zmieniona po instalacji. Będzie on Ręczne wyłączanie klienta z otrzymywania linków do najnowszej wersji. Program inicjujący poprawionej wersji nadal konieczne jest zaktualizowanie do określonej wersji na komputerze klienckim.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Jak zawsze włączone obsługi punktu odniesienia

Po aktualizacji do obsługi punktu odniesienia poprawionej wersji programu inicjującego pliki są udostępniane dla obsługi aktualizacji z [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). Mogą one być używane w kilku scenariuszach.

Aby zainstalować administratorom wdrażanie za pomocą układu sieci, administrator będzie chcesz zaktualizować [lokalizacja układu](update-a-network-installation-of-visual-studio.md). Klienci, którzy są instalowane z lokalizacji będą otrzymywać powiadomienia aktualizacji. Jeśli aktualizacja musi zostać wdrożone na klientach, postępuj zgodnie z [w instrukcjach](update-a-network-installation-of-visual-studio.md#how-to-deploy-an-update-to-client-machines). Podczas modyfikowania "response.json" dla aktualizacji, nie należy dodawać dodatkowych obciążeń, składników lub języków. Zarządzanie ustawieniami tych musi odbywać się jako "Modyfikuj" wdrożenie po aktualizacji produktu. 

Jeśli jest on zainstalowany na podstawie internet, należy uruchomić nowy program inicjujący poprawionej wersji za pomocą `--channelUri` parametrem manifestu kanału nie istnieje na komputerze klienckim. Jeśli aktualizacja jest wdrażana w trybie cichym lub pasywnym, należy użyć dwóch oddzielnych poleceń:

1. Po pierwsze Aktualizacja Instalatora programu Visual Studio: <br>```vs_enterprise.exe --quiet --update```
2. Następnie zaktualizuj samej aplikacji programu Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Podręcznik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](tools-for-managing-visual-studio-instances.md)
* [Jak definiować ustawienia w pliku odpowiedzi](automated-installation-with-response-file.md)
* [Sterowanie aktualizacjami na potrzeby wdrożenia oparte na sieci programu Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Cyklu życia produktu Visual Studio i obsługa](/visualstudio/releases/2019/servicing/)
