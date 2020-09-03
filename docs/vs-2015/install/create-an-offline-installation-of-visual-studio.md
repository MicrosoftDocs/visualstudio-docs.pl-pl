---
title: Tworzenie instalacji w trybie offline | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a6a9707d517a8a43d9a9ca156a5f7291ecee9bee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "81445068"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Tworzenie instalacji w trybie offline programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [Tworzenie instalacji w trybie offline programu Visual Studio](/visualstudio/install/create-an-offline-installation-of-visual-studio) lub [Tworzenie instalacji sieciowej programu Visual Studio](/visualstudio/install/create-a-network-installation-of-visual-studio).

Na tej stronie opisano, jak zainstalować program Visual Studio 2015, gdy nie masz połączenia z Internetem. Aby jednak przeprowadzić instalację rozłączoną, należy najpierw utworzyć układ instalacji w trybie offline przy użyciu maszyny połączonej z Internetem. Oto jak to zrobić.

> [!IMPORTANT]
> Jeśli na maszynie w trybie offline jest uruchomiony system Windows 7 z dodatkiem SP1 lub Windows Server 2008 R2, zobacz specjalne instrukcje w sekcji [Rozwiązywanie problemów z instalacją w trybie offline](#BKMK_tshoot) w tym temacie.  *Przed* zainstalowaniem programu Visual Studio 2015 należy wykonać te instrukcje.

## <a name="installing-by-creating-an-offline-installation"></a><a name="BKMK_Offline"></a> Instalowanie przez tworzenie instalacji w trybie offline

#### <a name="to-create-an-offline-installation-layout"></a>Aby utworzyć układ instalacji w trybie offline

1. Wybierz wersję programu Visual Studio, którą chcesz zainstalować, ze strony pobierania  [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) .

2. Po pobraniu instalatora do lokalizacji w systemie plików uruchom polecenie " \<executable name> /layout".

     Na przykład uruchom polecenie: `vs_enterprise.exe /layout D:\VisualStudio2015`

     Za pomocą `/layout` przełącznika można pobrać niemal wszystkie pakiety instalacyjne, a nie tylko te, które dotyczą komputera pobierania. Takie podejście umożliwia przekazanie plików potrzebnych do uruchomienia tego Instalatora w dowolnym miejscu i może być przydatne, jeśli chcesz zainstalować składniki, które nie zostały pierwotnie zainstalowane.

3. Po uruchomieniu tego polecenia pojawi się okno dialogowe, które pozwala zmienić folder, w którym ma się znajdować układ instalacji w trybie offline.   Następnie kliknij przycisk **Pobierz** .

     Po pomyślnym pobraniu pakietu powinien zostać wyświetlony komunikat informujący o **pomyślnym zakończeniu instalacji. Wszystkie określone składniki zostały pozyskane pomyślnie.**

4. Znajdź określony wcześniej folder. (Na przykład Znajdź D:\VisualStudio2015.) Ten folder zawiera wszystko, co jest potrzebne do kopiowania do udostępnionej lokalizacji lub instalacji nośnika.

    > [!CAUTION]
    > Obecnie Android SDK nie obsługuje środowiska instalacji w trybie offline. W przypadku instalowania Android SDK elementów instalacyjnych na komputerze, który nie jest połączony z Internetem, instalacja może zakończyć się niepowodzeniem. Aby uzyskać więcej informacji, zobacz sekcję "Rozwiązywanie problemów z instalacją w trybie offline" w tym temacie.

5. Uruchom instalację z lokalizacji pliku lub z nośnika instalacyjnego.

## <a name="updating-an-offline-installation"></a>Aktualizowanie instalacji w trybie offline
 Firma Microsoft udostępniła kilka aktualizacji dla programu Visual Studio 2015. Aby zaktualizować instalację programu Visual Studio, wystarczy pobrać wybraną wersję ze strony z witryny pobierania  [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) . Następnie postępuj zgodnie z instrukcjami przedstawionymi w tym temacie, aby utworzyć nowy układ instalacji w trybie offline, a następnie użyć go do zaktualizowania kopii programu Visual Studio 2015.

## <a name="troubleshooting-an-offline-installation"></a><a name="BKMK_tshoot"></a> Rozwiązywanie problemów z instalacją w trybie offline
 W przypadku instalowania w trybie offline z pamięci podręcznej instalacji w trybie offline może być widoczne komunikat ostrzegawczy informujący, że nie można zainstalować niektórych składników i pakietów. W poniższej tabeli przedstawiono możliwe rozwiązania tych scenariuszy.

| Składnik lub pakiet | Rozwiązanie |
|-|-|
| Dotfuscator i Analytics Community Edition 5.19.1 (dla wersji Community, Professional i Enterprise programu Visual Studio, zgodnie z zainstalowaną w **systemie Windows 7 z dodatkiem SP1** i **Windows Server 2008 R2**) | Jeśli na maszynie w trybie offline działa **system Windows 7 z dodatkiem SP1** lub **Windows Server 2008 R2**, przed zainstalowaniem programu Visual Studio 2015 należy wykonać następujące czynności:<br /><br /> 1. Skonfiguruj plik lub serwer sieci Web do pobierania plików CTL.<br /><br /> 2. Przekieruj adres URL aktualizacji automatycznych firmy Microsoft dla odłączonego środowiska.<br /><br /> Aby uzyskać więcej informacji, zobacz stronę [Konfigurowanie zaufanych katalogów głównych i niedozwolonych certyfikatów](https://technet.microsoft.com/library/dn265983.aspx) w witrynie Microsoft TechNet. |
| Konfiguracja Android SDK (poziom interfejsu API) | Do zainstalowania pakietów Android SDK (poziomu interfejsu API) wymagane jest połączenie internetowe. Jeśli używasz sieci z ograniczeniami, musisz zezwolić na dostęp do następujących adresów URL podczas instalacji programu Visual Studio:<br /><br /> -   `https://dl.google.com:443`<br />-   `https://dl-ssl.google.com:443`<br />-   `https://dl-ssl.google.com/android/repository/*`<br /> <br />Aby uzyskać więcej informacji o sposobach rozwiązywania potencjalnych problemów z ustawieniami serwera proxy, zobacz temat [Błędy instalacji programu Visual Studio 2015 (konfiguracja Android SDK) za wpisem na blogu serwera proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) . |
| Szablony elementów rozszerzalności programu Visual Studio<br /><br /> Rozszerzenia GitHub dla programu Visual Studio<br /><br /> Narzędzia programu PowerShell dla programu Visual Studio | Jeśli podczas instalowania programu Visual Studio 2015 nie ma połączenia z Internetem, można użyć specjalnego kanału informacyjnego offline w celu wygenerowania układu instalacji w trybie offline. **Uwaga:**  To specjalne źródło danych zawiera najnowsze aktualizacje programu Visual Studio 2015. <br /><br /> Aby utworzyć specjalne źródło danych w trybie offline, uruchom następujące polecenie:/layout *Drive:* \VisualStudio2015/overridefeeduri *URL-to-wysuw-XML*<br /><br /> Na przykład w przypadku specjalnych w języku angielskim kanału informacyjnego offline programu Visual Studio 2015 Enterprise Uruchom polecenie:<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "https://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Aby uzyskać pełną listę adresów URL, których można użyć do utworzenia specjalnego źródła offline w wybranym języku, zobacz poniższą tabelę. |

 Użyj następujących adresów URL, aby utworzyć specjalne źródło w trybie offline specyficzne dla języka, zgodnie z opisem w powyższej tabeli.

|       Język        |                            Adres URL                            |
|-----------------------|-----------------------------------------------------------|
| Chiński (uproszczony)  | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| Chiński (tradycyjny) | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         Czeski         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        niemiecki         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        Angielski        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        Hiszpański        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        Francuski         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        Włoski        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       japoński        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        koreański         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        Polski         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      Portugalski       | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        Rosyjski        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        Turecki        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>Zobacz też

- [Instalowanie programu Visual Studio](install-visual-studio-2015.md)