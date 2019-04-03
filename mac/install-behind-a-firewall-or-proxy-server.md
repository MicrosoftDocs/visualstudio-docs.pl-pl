---
title: Instalowanie i używanie programu Visual Studio dla komputerów Mac za serwerem zapory lub serwera proxy
description: Ten dokument zawiera listę hostów, które muszą być na liście dozwolonych w taki sposób, aby zezwolić na program Visual Studio for Mac (i jego obciążeń, w tym Xamarin) do pracy w środowisku firmowym.
ms.topic: troubleshooting
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: asb3993
ms.author: amburns
ms.date: 10/23/2018
ms.openlocfilehash: bf12f8803fbdbbf1de31899501c31545a09d6b09
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58856544"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalowanie i używanie programu Visual Studio dla komputerów Mac za serwerem zapory lub serwera proxy

Jeśli Ty lub Twoja organizacja korzysta z środki bezpieczeństwa, takie jak Zapora lub serwer proxy, następnie istnieją adresy URL domen, które możesz chcieć "dozwolonych" i porty i protokoły, które można otworzyć, aby mieć najlepsze wyniki, podczas instalacji i używania Visual Stu dio dla systemów Mac i usług platformy Azure.

- [**Zainstaluj program Visual Studio dla komputerów Mac**](#install-visual-studio-for-mac): Te tabele zawierają adresy URL do listy dozwolonych adresów, tak, aby mieć dostęp do wszystkich funkcji i obciążeń programu Visual Studio dla komputerów Mac.

- [**Użyj programu Visual Studio dla komputerów Mac**](#use-visual-studio-for-mac): Te tabele zawierają adresy URL do listy dozwolonych adresów, tak, aby mieć dostęp do wszystkich usług i funkcji, które chcesz.

## <a name="install-visual-studio-for-mac"></a>Zainstaluj program Visual Studio dla komputerów Mac

Ponieważ programu Visual Studio dla komputerów Mac, Instalator pobierze z różnych domen i pobrać serwerów, w tym miejscu są domenach i adresach URL, które chcesz dodać jako zaufany w konfiguracjach.

### <a name="microsoft-domains"></a>Microsoft domains

| Domain| Cel |
| ----------------------------------- |---------------------------|
| *.live.com| Credential Management |
| app.vssps.visualstudio.com| Instalator metadanych|
| vortex.data.microsoft.com | O awariach i raportowanie błędów |
| az667904.vo.msecnd.net| O awariach i raportowanie błędów |
| xamarin.com | Instalator metadanych|
| xampubdl.blob.core.windows.net| Pakiety instalacyjne|
| download.visualstudio.microsoft.com | Pakiety instalacyjne|
| xamarin.azureedge.net | Pakiety instalacyjne|
| developer.xamarin.com | Pakiety instalacyjne|
| dc.services.visualstudio.com| Raporty o awariach |

### <a name="third-party-domains"></a>Domeny innej firmy

| Domain| Cel |
| --------------------------|-------------------------|
| dl.google.com | Android SDK |
| download.oracle.com | Java SDK|
| api.apple-cloudkit.com| Usługi zabezpieczeń firmy Apple |

## <a name="use-visual-studio-for-mac"></a>Use Visual Studio for Mac

Aby upewnić się, że masz dostęp do wszystkich funkcji, które są potrzebne w programie Visual Studio dla komputerów Mac podczas używany serwer proxy lub zapora, firma Microsoft zaleca umieszczeniu na białej liście następujących domen i portów.

### <a name="general"></a>Ogólne

| Domain | Porty|Cel|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Rozpoznawanie adresu URL firmy Microsoft |
| vsstartpage.blob.core.windows.net| 80/443| Rozpocznij strony danych|
| software.xamarin.com |  80/443|Usługę aktualizacji|
| addins.monodevelop.com | 80/443| Rozszerzenie usług |
| visualstudio-devdiv-c2s.msedge.net | 80/443| Funkcja eksperymentalna i powiadomienia |
| targetednotifications.azurewebsites.net|  80/443| Używane do filtrowania globalną listę powiadomień do listy, która ma zastosowanie tylko do określonych rodzajów scenariusze maszyn/użycia|

### <a name="identity"></a>Tożsamość

| Domain | Porty|Cel|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| Dostawcy tożsamości|
| secure.aadcdn.microsoftonline-p.com | 80/443|Dostawcy tożsamości|
| dc.services.visualstudio.com| 80/443|Raporty o awariach|
| management.azure.com|80/443| Interfejs API usług platformy Azure |

### <a name="nuget"></a>NuGet

| Domain | Porty|Cel|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|Interfejs API programu NuGet|
| secure.aadcdn.microsoftonline-p.com |80/443| Dostawcy tożsamości|

### <a name="android-projects"></a>Projekty systemu android

| Domain| Cel|
| ------------------------------------|------------------------------------|
| time.android.com| Serwer czasu dla emulatora systemu Android |
| connectivitycheck.gstatic.com | Połączenia dla emulatora systemu Android|
| cloudconfig.googleapis.com| Interfejsy API w emulatorze systemu Android|

## <a name="see-also"></a>Zobacz także

- [Instalowanie i używanie programu Visual Studio i usług platformy Azure za serwerem zapory lub serwera proxy](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Rozwiązywanie problemów z podobne problemy w Windows](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
