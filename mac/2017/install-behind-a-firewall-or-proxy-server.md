---
title: Instalowanie i używanie programu Visual Studio dla komputerów Mac za zaporą lub serwerem proxy
description: Ten dokument zawiera listę hostów, które muszą być dozwolone w zaporze, aby umożliwić programowi Visual Studio dla komputerów Mac (i jego obciążeń, w tym platformy Xamarin) do pracy w środowisku firmowym.
ms.topic: troubleshooting
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: heiligerdankgesang
ms.author: dominicn
ms.date: 10/23/2018
ms.openlocfilehash: 738c5277ca6a669a834635f5c626e0cbabd7a7ef
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984941"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalowanie i używanie programu Visual Studio dla komputerów Mac za zaporą lub serwerem proxy

Jeśli ty lub Twoja organizacja używa środków bezpieczeństwa, takich jak zapora lub serwer proxy, istnieją domeny, które można dodać do "listy dozwolonych" oraz porty i protokoły, które można otworzyć, aby uzyskać najlepsze wrażenia podczas instalacji i używania Visual Studio dla komputerów Mac i usług Platformy Azure.

- [**Zainstaluj program Visual Studio dla komputerów Mac:**](#install-visual-studio-for-mac)Te tabele zawierają domeny, które muszą zezwalać na łączność, aby mieć dostęp do wszystkich funkcji i obciążeń programu Visual Studio dla komputerów Mac.

- [**Użyj programu Visual Studio dla komputerów Mac:**](#use-visual-studio-for-mac)Te tabele zawierają domeny, które muszą zezwalać na łączność, aby mieć dostęp do powiązanych funkcji.

## <a name="install-visual-studio-for-mac"></a>Instalowanie programu Visual Studio dla komputerów Mac

Ponieważ Instalator programu Visual Studio dla komputerów Mac pobiera z różnych domen i pobiera serwery, oto domeny i adresy URL, które można dodać jako zaufane w konfiguracjach.

### <a name="microsoft-domains"></a>Domeny firmy Microsoft

| Domain| Przeznaczenie |
| ----------------------------------- |---------------------------|
| *.live.com| Zarządzanie poświadczeniami |
| app.vssps.visualstudio.com| Metadane instalatora|
| vortex.data.microsoft.com | Raportowanie awarii i błędów |
| az667904.vo.msecnd.net| Raportowanie awarii i błędów |
| xamarin.com | Metadane instalatora|
| xampubdl.blob.core.windows.net| Pakiety instalatora|
| download.visualstudio.microsoft.com | Pakiety instalatora|
| xamarin.azureedge.net | Pakiety instalatora|
| developer.xamarin.com | Pakiety instalatora|
| dc.services.visualstudio.com| Raportowanie awarii |

### <a name="third-party-domains"></a>Domeny innych firm

| Domain| Przeznaczenie |
| --------------------------|-------------------------|
| dl.google.com | Android SDK |
| download.oracle.com | Zestaw SDK Java|
| api.apple-cloudkit.com| Usługi zabezpieczeń Firmy Apple |

## <a name="use-visual-studio-for-mac"></a>Korzystanie z programu Visual Studio dla komputerów Mac

Aby upewnić się, że masz dostęp do każdej funkcji, które są potrzebne w programie Visual Studio dla komputerów Mac, gdy za serwerem proxy lub zaporą, zaleca się dodanie następujących domen i portów do listy dozwolonego dostępu.

### <a name="general"></a>Ogólne

| Domain | Porty|Przeznaczenie|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Rozpoznawanie adresów URL firmy Microsoft |
| vsstartpage.blob.core.windows.net| 80/443| Uruchom dane strony|
| software.xamarin.com |  80/443|Usługa updater|
| addins.monodevelop.com | 80/443| Usługi rozszerzeń |
| visualstudio-devdiv-c2s.msedge.net | 80/443| Funkcja eksperymentalna i powiadomienia |
| targetednotifications.azurewebsites.net|  80/443| Służy do filtrowania globalnej listy powiadomień do listy, która ma zastosowanie tylko do określonych typów maszyn/scenariuszy użycia|

### <a name="identity"></a>Tożsamość

| Domain | Porty|Przeznaczenie|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| Dostawca tożsamości|
| secure.aadcdn.microsoftonline-p.com | 80/443|Dostawca tożsamości|
| dc.services.visualstudio.com| 80/443|Raportowanie awarii|
| management.azure.com|80/443| Interfejs API usług platformy Azure |

### <a name="nuget"></a>NuGet

| Domain | Porty|Przeznaczenie|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|Interfejs API narzędzia NuGet|
| secure.aadcdn.microsoftonline-p.com |80/443| Dostawca tożsamości|

### <a name="android-projects"></a>Projekty na Androida

| Domain| Przeznaczenie|
| ------------------------------------|------------------------------------|
| time.android.com| Serwer czasu dla emulatora systemu Android |
| connectivitycheck.gstatic.com | Łączność dla emulatora Androida|
| cloudconfig.googleapis.com| Interfejsy API dla emulatora systemu Android|

## <a name="see-also"></a>Zobacz też

- [Instalowanie i używanie usług Visual Studio 2017 i usługi Azure za zaporą lub serwerem proxy](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Rozwiązywanie podobnych problemów w systemie Windows](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
