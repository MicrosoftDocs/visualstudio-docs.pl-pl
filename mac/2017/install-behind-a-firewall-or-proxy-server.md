---
title: Instalowanie i używanie Visual Studio dla komputerów Mac za zaporą lub serwerem proxy
description: Ten dokument zawiera listę hostów, które muszą być dozwolone w zaporze, aby umożliwić działanie Visual Studio dla komputerów Mac (i jego obciążeń, w tym Xamarin), do pracy w środowisku firmowym.
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: heiligerdankgesang
ms.author: dominicn
ms.date: 10/23/2018
ms.openlocfilehash: d488d56bdecd2801ecd94a2551c3be0f9834d0d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85938676"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalowanie i używanie Visual Studio dla komputerów Mac za zaporą lub serwerem proxy

Jeśli ty lub Twoja organizacja korzysta z środków zabezpieczeń, takich jak zapora lub serwer proxy, istnieją domeny, które możesz chcieć dodać do listy "dozwolony list" i portów i protokołów, które mogą być otwierane, dzięki czemu będziesz mieć najlepsze środowisko w przypadku instalowania i używania usług Visual Studio dla komputerów Mac i Azure.

- [**Zainstaluj Visual Studio dla komputerów Mac**](#install-visual-studio-for-mac): te tabele obejmują domeny, które muszą zezwalać na łączność, aby mieć dostęp do wszystkich funkcji i obciążeń Visual Studio dla komputerów Mac.

- [**Użyj Visual Studio dla komputerów Mac**](#use-visual-studio-for-mac): te tabele obejmują domeny, które muszą zezwalać na łączność, aby mieć dostęp do pokrewnych funkcji.

## <a name="install-visual-studio-for-mac"></a>Instalowanie programu Visual Studio dla komputerów Mac

Ponieważ Instalator Visual Studio dla komputerów Mac pobiera z różnych domen i pobiera serwery, poniżej znajdują się domeny i adresy URL, które mogą być dodawane jako zaufane w konfiguracjach.

### <a name="microsoft-domains"></a>Domeny firmy Microsoft

| Domena| Przeznaczenie |
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
| dc.services.visualstudio.com| Raportowanie awarii |

### <a name="third-party-domains"></a>Domeny innych firm

| Domena| Przeznaczenie |
| --------------------------|-------------------------|
| dl.google.com | Android SDK |
| download.oracle.com | Zestaw SDK Java|
| api.apple-cloudkit.com| Usługi zabezpieczeń firmy Apple |

## <a name="use-visual-studio-for-mac"></a>Korzystanie z programu Visual Studio dla komputerów Mac

Aby upewnić się, że masz dostęp do wszystkich funkcji, które są potrzebne w Visual Studio dla komputerów Macj za serwerem proxy lub zaporą, zalecamy dodanie następujących domen i portów do listy dozwolonych dostępów.

### <a name="general"></a>Ogólne

| Domena | Porty|Przeznaczenie|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Rozpoznawanie adresów URL firmy Microsoft |
| vsstartpage.blob.core.windows.net| 80/443| Dane strony początkowej|
| software.xamarin.com |  80/443|Usługa Aktualizator|
| addins.monodevelop.com | 80/443| Usługi rozszerzeń |
| visualstudio-devdiv-c2s.msedge.net | 80/443| Eksperymentalna funkcja i powiadomienia |
| targetednotifications.azurewebsites.net|  80/443| Służy do filtrowania globalnej listy powiadomień do listy, która ma zastosowanie tylko do określonych typów maszyn/scenariuszy użycia|

### <a name="identity"></a>Tożsamość

| Domena | Porty|Przeznaczenie|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| Dostawca tożsamości|
| secure.aadcdn.microsoftonline-p.com | 80/443|Dostawca tożsamości|
| dc.services.visualstudio.com| 80/443|Raportowanie awarii|
| management.azure.com|80/443| Interfejs API usług platformy Azure |

### <a name="nuget"></a>NuGet

| Domena | Porty|Przeznaczenie|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|Interfejs API narzędzia NuGet|
| secure.aadcdn.microsoftonline-p.com |80/443| Dostawca tożsamości|

### <a name="android-projects"></a>Projekty systemu Android

| Domena| Przeznaczenie|
| ------------------------------------|------------------------------------|
| time.android.com| Serwer czasu dla Emulator systemu Android |
| connectivitycheck.gstatic.com | Łączność dla Emulator systemu Android|
| cloudconfig.googleapis.com| Interfejsy API dla Emulator systemu Android|

## <a name="see-also"></a>Zobacz też

- [Instalowanie i używanie programu Visual Studio 2017 i usług platformy Azure za zaporą lub serwerem proxy](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Rozwiązywanie podobnych problemów w systemie Windows](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
