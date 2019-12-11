---
title: Instalowanie i używanie Visual Studio dla komputerów Mac za zaporą lub serwerem proxy
description: Ten dokument zawiera listę hostów, które muszą być dozwolone w zaporze, aby umożliwić działanie Visual Studio dla komputerów Mac (i jego obciążeń, w tym Xamarin), do pracy w środowisku firmowym.
ms.topic: troubleshooting
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.openlocfilehash: 717eb9cd58f213c3d2c31a18c546a83ab8feb645
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984032"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalowanie i używanie Visual Studio dla komputerów Mac za zaporą lub serwerem proxy

Jeśli ty lub Twoja organizacja korzysta z środków bezpieczeństwa, takich jak zapora lub serwer proxy, istnieją domeny, które możesz chcieć dodać do listy "Lista dozwolonych" oraz portów i protokołów, które mogą być otwierane w celu uzyskania najlepszego środowiska podczas instalacji i używania rejestrowania dostępu użytkowników Studio for Mac i usługi platformy Azure.

- [**Zainstaluj Visual Studio dla komputerów Mac**](#install-visual-studio-for-mac): te tabele obejmują domeny, które muszą zezwalać na łączność, aby mieć dostęp do wszystkich funkcji i obciążeń Visual Studio dla komputerów Mac.

- [**Użyj Visual Studio dla komputerów Mac**](#use-visual-studio-for-mac): te tabele obejmują domeny, które muszą zezwalać na łączność, aby mieć dostęp do pokrewnych funkcji.

## <a name="install-visual-studio-for-mac"></a>Instalowanie programu Visual Studio dla komputerów Mac

Ponieważ Instalator Visual Studio dla komputerów Mac pobiera z różnych domen i pobiera serwery, poniżej znajdują się domeny i adresy URL, które mogą być dodawane jako zaufane w konfiguracjach.

### <a name="microsoft-domains"></a>Microsoft domains

| Domena| Cel |
| ----------------------------------- |---------------------------|
| *.live.com| Zarządzanie poświadczeniami |
| app.vssps.visualstudio.com| Metadane Instalatora|
| vortex.data.microsoft.com | Raportowanie awarii i błędów |
| az667904.vo.msecnd.net| Raportowanie awarii i błędów |
| xamarin.com | Metadane Instalatora|
| xampubdl.blob.core.windows.net| Pakiety Instalatora|
| download.visualstudio.microsoft.com | Pakiety Instalatora|
| xamarin.azureedge.net | Pakiety Instalatora|
| developer.xamarin.com | Pakiety Instalatora|
| static.xamarin.com | Pakiety Instalatora|
| dl.xamarin.com | Pakiety Instalatora|
| dc.services.visualstudio.com| Raporty o awariach |

### <a name="third-party-domains"></a>Domeny innych firm

| Domena| Cel |
| --------------------------|-------------------------|
| dl.google.com | Android SDK |
| download.oracle.com | Zestaw Java SDK|
| api.apple-cloudkit.com| Usługi zabezpieczeń firmy Apple |

## <a name="use-visual-studio-for-mac"></a>Użyj Visual Studio dla komputerów Mac

Aby upewnić się, że masz dostęp do wszystkich funkcji, które są potrzebne w Visual Studio dla komputerów Macj za serwerem proxy lub zaporą, zalecamy dodanie następujących domen i portów do listy dozwolonych dostępów.

### <a name="general"></a>Ogólne

| Domena | Porty|Cel|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Rozpoznawanie adresów URL firmy Microsoft |
| vsstartpage.blob.core.windows.net| 80/443| Dane strony początkowej|
| software.xamarin.com |  80/443|Usługa Aktualizator|
| addins.monodevelop.com | 80/443| Usługi rozszerzeń |
| visualstudio-devdiv-c2s.msedge.net | 80/443| Eksperymentalna funkcja i powiadomienia |
| targetednotifications.azurewebsites.net|  80/443| Używane do filtrowania globalną listę powiadomień do listy, która ma zastosowanie tylko do określonych rodzajów scenariusze maszyn/użycia|

### <a name="identity"></a>Tożsamość

| Domena | Porty|Cel|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| Dostawca tożsamości|
| secure.aadcdn.microsoftonline-p.com | 80/443|Dostawca tożsamości|
| dc.services.visualstudio.com| 80/443|Raporty o awariach|
| management.azure.com|80/443| Interfejs API usług platformy Azure |

### <a name="nuget"></a>NuGet

| Domena | Porty|Cel|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|Interfejs API narzędzia NuGet|
| secure.aadcdn.microsoftonline-p.com |80/443| Dostawca tożsamości|

### <a name="android-projects"></a>Projekty systemu Android

| Domena| Cel|
| ------------------------------------|------------------------------------|
| time.android.com| Serwer czasu dla Emulator systemu Android |
| connectivitycheck.gstatic.com | Łączność dla Emulator systemu Android|
| cloudconfig.googleapis.com| Interfejsy API dla Emulator systemu Android|

## <a name="see-also"></a>Zobacz także

- [Instalowanie i używanie programu Visual Studio i usług platformy Azure za serwerem zapory lub serwera proxy](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Rozwiązywanie podobnych problemów w systemie Windows](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
