---
title: Tworzenie instalacji w trybie offline | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445068"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Tworzenie instalacji w trybie offline programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację dotyczącą programu Visual Studio, zobacz [Tworzenie instalacji programu Visual Studio w trybie offline](/visualstudio/install/create-an-offline-installation-of-visual-studio) lub [Tworzenie instalacji sieciowej programu Visual Studio.](/visualstudio/install/create-a-network-installation-of-visual-studio)

Na tej stronie opisano sposób instalowania programu Visual Studio 2015, gdy nie masz połączenia z Internetem. Jednak aby wykonać instalację "odłączoną", należy najpierw utworzyć układ instalacji w trybie offline przy użyciu komputera podłączonego do Internetu. Oto jak to zrobić.

> [!IMPORTANT]
> Jeśli na komputerze w trybie offline jest uruchomiony system Windows 7 z dodatkiem SP1 lub Windows Server 2008 R2, zapoznaj się ze specjalnymi instrukcjami w sekcji Rozwiązywanie problemów z [instalacją w trybie offline](#BKMK_tshoot) w tym temacie.  Przed zainstalowaniem programu Visual Studio 2015 należy wykonać te *instrukcje.*

## <a name="installing-by-creating-an-offline-installation"></a><a name="BKMK_Offline"></a>Instalowanie przez utworzenie instalacji w trybie offline

#### <a name="to-create-an-offline-installation-layout"></a>Aby utworzyć układ instalacji w trybie offline

1. Wybierz wersję programu Visual Studio, którą chcesz zainstalować, ze strony [pobierania My.VisualStudio.com.](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015)

2. Po pobraniu instalatora do lokalizacji w systemie\<plików uruchom "nazwę wykonywalną> /layout".

     Na przykład uruchom:`vs_enterprise.exe /layout D:\VisualStudio2015`

     Za pomocą `/layout` przełącznika można pobrać prawie wszystkie pakiety instalacyjne, a nie tylko te, które mają zastosowanie do komputera do pobrania. Takie podejście zapewnia pliki, które należy uruchomić tego instalatora w dowolnym miejscu i może być przydatne, jeśli chcesz zainstalować składniki, które nie zostały zainstalowane pierwotnie.

3. Po uruchomieniu tego polecenia pojawi się okno dialogowe umożliwiające zmianę folderu, w którym ma się znajdujeć układ instalacji w trybie offline.   Następnie kliknij przycisk **Pobierz.**

     Po pomyślnym pobraniu pakietu powinien zostać wyświetlony komunikat z informacją **O pomyślnym zakończeniu instalacji! Wszystkie określone składniki zostały pomyślnie nabyte.**

4. Zlokalizuj folder określony wcześniej. (Na przykład znajdź D:\VisualStudio2015.) Ten folder zawiera wszystko, co jest potrzebne do skopiowania do udostępnionej lokalizacji lub zainstalowania nośnika.

    > [!CAUTION]
    > Obecnie zestaw SDK systemu Android nie obsługuje instalacji w trybie offline. Jeśli zainstalujesz elementy Instalatora SDK systemu Android na komputerze, który nie jest połączony z Internetem, instalacja może zakończyć się niepowodzeniem. Aby uzyskać więcej informacji, zobacz sekcję "Rozwiązywanie problemów z instalacją w trybie offline" w tym temacie.

5. Uruchom instalację z lokalizacji pliku lub z nośnika instalacyjnego.

## <a name="updating-an-offline-installation"></a>Aktualizowanie instalacji w trybie offline
 Firma Microsoft wydała kilka aktualizacji dla programu Visual Studio 2015. Aby zaktualizować instalację programu Visual Studio, po prostu pobierz odpowiednią wersję ze strony [pobierania My.VisualStudio.com.](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) Następnie wykonaj kroki opisane w tym temacie, aby utworzyć nowy układ instalacji w trybie offline, a następnie użyj go do zaktualizowania kopii programu Visual Studio 2015.

## <a name="troubleshooting-an-offline-installation"></a><a name="BKMK_tshoot"></a>Rozwiązywanie problemów z instalacją w trybie offline
 Po zainstalowaniu w trybie offline z pamięci podręcznej instalacji w trybie offline mogą pojawić się komunikaty ostrzegawcze o nieuiszczenie instalacji niektórych składników i pakietów. Poniższa tabela zawiera możliwe rozwiązania dla tych scenariuszy.

| Komponent lub pakiet | Rozwiązanie |
|-|-|
| Dotfuscator i Analytics Community Edition 5.19.1 (dla wersji Community, Professional i Enterprise programu Visual Studio, zainstalowanych w **systemach Windows 7 z sp1** i **Windows Server 2008 R2)** | Jeśli na komputerze w trybie offline jest uruchomiony **system Windows 7 z sp1** lub **Windows Server 2008 R2,** przed zainstalowaniem programu Visual Studio 2015 należy wykonać następujące czynności:<br /><br /> 1. Skonfiguruj plik lub serwer www, aby pobrać pliki CTL.<br /><br /> 2. Przekieruj adres URL automatycznej aktualizacji firmy Microsoft dla środowiska rozłączone.<br /><br /> Aby uzyskać więcej informacji, zobacz stronę [Konfigurowanie zaufanych katalogów głównych i niedozwolonych certyfikatów](https://technet.microsoft.com/library/dn265983.aspx) w witrynie Microsoft TechNet. |
| Instalator SDK systemu Android (poziom interfejsu API) | Aby zainstalować pakiety SDK systemu Android (API Level), musisz mieć połączenie z Internetem. Jeśli korzystasz z sieci z ograniczeniami, podczas instalowania programu Visual Studio należy zezwolić na dostęp do następujących adresów URL:<br /><br /> -   `https://dl.google.com:443`<br />-   `https://dl-ssl.google.com:443`<br />-   `https://dl-ssl.google.com/android/repository/*`<br /> <br />Aby uzyskać więcej informacji na temat rozwiązywania możliwych problemów z ustawieniami serwera proxy, zobacz [błędy instalacji programu Visual Studio 2015 (Instalator sdk systemu Android) za wpisem](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) w blogu serwera proxy. |
| Szablony elementów rozszerzalności programu Visual Studio<br /><br /> Rozszerzenia GitHub dla programu Visual Studio<br /><br /> Narzędzia programu PowerShell dla programu Visual Studio | Jeśli podczas instalowania programu Visual Studio 2015 nie masz połączenia z Internetem, można użyć specjalnego kanału informacyjnego w trybie offline do wygenerowania układu instalacji w trybie offline. **Uwaga:**  Ten specjalny kanał informacyjny zawiera najnowsze aktualizacje programu Visual Studio 2015. <br /><br /> Aby utworzyć specjalny kanał informacyjny w trybie offline, uruchom następujące polecenie: /layout *Drive:* \VisualStudio2015 /overridefeeduri *URL-to-feed-xml*<br /><br /> Na przykład dla anglojęzycznego specjalnego kanału informacyjnego w trybie offline programu Visual Studio 2015 Enterprise uruchom:<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "https://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Aby uzyskać pełną listę adresów URL, których można użyć do utworzenia specjalnego kanału informacyjnego offline w wybranym języku, zobacz poniższą tabelę. |

 Użyj następujących adresów URL, aby utworzyć specjalny plik danych offline specyficzny dla danego języka, zgodnie z opisem w powyższej tabeli.

|       Język        |                            Adres URL                            |
|-----------------------|-----------------------------------------------------------|
| Chiński uproszczony  | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| Chiński (tradycyjny) | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         Czeski         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        Niemiecki         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        Polski        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        Hiszpański        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        Francuski         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        Włoski        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       Japoński        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        Koreański         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        Polski         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      Portugalski       | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        Rosyjski        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        Turecki        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>Zobacz też

- [Instalowanie programu Visual Studio](install-visual-studio-2015.md)