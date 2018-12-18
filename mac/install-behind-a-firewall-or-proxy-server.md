---
title: Instalowanie i używanie programu Visual Studio dla komputerów Mac za serwerem zapory lub serwera proxy
description: Ten dokument zawiera listę hostów, które muszą być na liście dozwolonych w taki sposób, aby zezwolić na program Visual Studio for Mac (i jego obciążeń, w tym Xamarin) do pracy w środowisku firmowym.
ms.topic: troubleshooting
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: asb3993
ms.author: amburns
ms.date: 10/23/2018
ms.openlocfilehash: 70ac8defdcea9cccd8a3b3f9be71d38fb78c9c50
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295198"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalowanie i używanie programu Visual Studio dla komputerów Mac za serwerem zapory lub serwera proxy

Jeśli Ty lub Twoja organizacja korzysta z środki bezpieczeństwa, takie jak Zapora lub serwer proxy, następnie istnieją adresy URL domen, które możesz chcieć "dozwolonych" i porty i protokoły, które można otworzyć, aby mieć najlepsze wyniki, podczas instalacji i używania Visual Stu dio dla systemów Mac i usług platformy Azure.

- [**Zainstaluj program Visual Studio dla komputerów Mac**](#install-visual-studio-for-mac): te tabele zawierają adresy URL do listy dozwolonych adresów, tak, aby mieć dostęp do wszystkich funkcji i obciążeń programu Visual Studio dla komputerów Mac.

- [**Użyj programu Visual Studio dla komputerów Mac**](#use-visual-studio-for-mac): te tabele tak, aby mieć dostęp do wszystkich usług i funkcji, które chcesz uwzględnić adresów URL do listy dozwolonych adresów.

## <a name="install-visual-studio-for-mac"></a>Zainstaluj program Visual Studio dla komputerów Mac

Ponieważ programu Visual Studio dla komputerów Mac, Instalator pobierze z różnych domen i pobrać serwerów, w tym miejscu są domenach i adresach URL, które chcesz dodać jako zaufany w konfiguracjach.

### <a name="microsoft-domains"></a>Microsoft domains

| Domain| Cel |
| ----------------------------------- |---------------------------|
| *.live.com| Zarządzanie poświadczeniami |
| app.vssps.visualstudio.com| Instalator metadanych|
| vortex.data.microsoft.com | O awariach i raportowanie błędów |
| az667904.vo.msecnd.net| O awariach i raportowanie błędów |
| strony xamarin.com | Instalator metadanych|
| xampubdl.blob.Core.Windows.NET| Pakiety instalacyjne|
| download.visualstudio.microsoft.com | Pakiety instalacyjne|
| xamarin.azureedge.NET | Pakiety instalacyjne|
| Developer.xamarin.com | Pakiety instalacyjne|
| dc.services.visualstudio.com| Raporty o awariach |

### <a name="third-party-domains"></a>Domeny innej firmy

| Domain| Cel |
| --------------------------|-------------------------|
| dl.google.com | Android SDK |
| download.oracle.com | Java SDK|
| API.Apple cloudkit.com| Usługi zabezpieczeń firmy Apple |

## <a name="use-visual-studio-for-mac"></a>Użyj programu Visual Studio dla komputerów Mac

Aby upewnić się, że masz dostęp do wszystkich funkcji, które są potrzebne w programie Visual Studio dla komputerów Mac podczas używany serwer proxy lub zapora, firma Microsoft zaleca umieszczeniu na białej liście następujących domen i portów.

### <a name="general"></a>Ogólne

| Domain | Porty|Cel|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Rozpoznawanie adresu URL firmy Microsoft |
| vsstartpage.blob.core.windows.net| 80/443| Rozpocznij strony danych|
| Software.xamarin.com |  80/443|Usługę aktualizacji|
| AddIns.monodevelop.com | 80/443| Rozszerzenie usług |
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
| API.nuget.org | 80/443|Interfejs API programu NuGet|
| secure.aadcdn.microsoftonline-p.com |80/443| Dostawcy tożsamości|

### <a name="android-projects"></a>Projekty systemu android

| Domain| Cel|
| ------------------------------------|------------------------------------|
| Time.android.com| Serwer czasu dla emulatora systemu Android |
| connectivitycheck.gstatic.com | Połączenia dla emulatora systemu Android|
| cloudconfig.googleapis.com| Interfejsy API w emulatorze systemu Android|

## <a name="see-also"></a>Zobacz także

- [Instalowanie i używanie usług platformy Azure i programu Visual Studio 2017 za serwerem zapory lub serwera proxy](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Rozwiązywanie problemów z podobne problemy w Windows](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
