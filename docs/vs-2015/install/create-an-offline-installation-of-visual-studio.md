---
title: Tworzenie instalacji w trybie Offline | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 8d76e4b1c9a7f7b6882eccab4a250e95c7419ea0
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54763136"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Tworzenie instalacji Offline programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio 2017, zobacz [instalacji programu Visual Studio 2017 w powolnych lub zawodnych środowiskach sieciowych](https://docs.microsoft.com/visualstudio/install/install-vs-inconsistent-quality-network), lub [Tworzenie instalacji sieciowej programu Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/create-a-network-installation-of-visual-studio) i [Specjalne uwagi dotyczące instalowania programu Visual Studio 2017 w trybie offline środowiska](https://docs.microsoft.com/visualstudio/install/install-visual-studio-in-offline-environment).

Ta strona w tym artykule opisano sposób instalowania programu Visual Studio 2015, gdy nie jest połączony z Internetem. Jednak aby przeprowadzić instalację "odłączonego", należy najpierw utworzyć układu instalacji w trybie offline przy użyciu komputerze, na którym jest połączony z Internetem. Oto jak to zrobić.

> [!IMPORTANT]
>  Jeśli maszyny w trybie offline jest uruchomiona, Windows 7 z dodatkiem SP1 lub Windows Server 2008 R2, zobacz instrukcje specjalne [Rozwiązywanie problemów z instalacją w trybie offline](#BKMK_tshoot) części tego tematu.  Wykonaj te instrukcje *przed* instalacji programu Visual Studio 2015.

##  <a name="BKMK_Offline"></a> Instalowanie przez tworzenie instalacji w trybie offline

#### <a name="to-create-an-offline-installation-layout"></a>Aby utworzyć układ instalacji w trybie offline

1.  Wybierz wersję programu Visual Studio, który chcesz zainstalować z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) strony pobierania.

2.  Po pobraniu Instalatora w lokalizacji w systemie plików Uruchom "\<nazwą pliku wykonywalnego >/layout".

     Na przykład uruchomić: `vs_enterprise.exe /layout D:\VisualStudio2015`

     Za pomocą `/layout` przełącznika, możesz pobrać prawie wszystkich pakietów instalacyjnych, nie tylko tych, które dotyczą komputera pobierania. Takie podejście zapewnia pliki, które należy uruchom tego Instalatora w dowolnym miejscu i może być przydatne, jeśli chcesz zainstalować składniki, które pierwotnie nie instalowano.

3.  Po uruchomieniu tego polecenia, zostanie wyświetlone okno dialogowe, które pozwala zmienić folder, w którym ma układu instalacji w trybie offline, aby znajdują się.   Następnie kliknij przycisk **Pobierz** przycisku.

     Jeśli pobieranie pakietu zakończy się pomyślnie, powinien zostać wyświetlony komunikat informujący, że **Instalacja zakończona pomyślnie! Pomyślnie pobrano wszystkie określone składniki.**

4.  Zlokalizuj folder, w którym określone wcześniej. (Na przykład zlokalizuj D:\VisualStudio2015). Ten folder zawiera wszystko, czego potrzebujesz, aby skopiować do współdzielonej lokalizacji lub nośnika instalacyjnego.

    > [!CAUTION]
    >  Zestaw SDK systemu Android nie obsługuje obecnie środowisko instalacji w trybie offline. Jeśli elementy Instalacja zestawu Android SDK można zainstalować na komputerze, który nie jest połączony z Internetem, instalacja może zakończyć się niepowodzeniem. Aby uzyskać więcej informacji zobacz sekcję "Rozwiązywanie problemów z instalacją w trybie offline", w tym temacie.

5.  Uruchom instalację z lokalizacji pliku lub nośnika instalacyjnego.

## <a name="updating-an-offline-installation"></a>Aktualizowanie instalacji w trybie offline
 Firma Microsoft wydała kilka aktualizacji dla programu Visual Studio 2015. Aby zaktualizować instalację programu Visual Studio, wystarczy pobrać wersję z z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) strony pobierania. Następnie wykonaj czynności opisane w tym temacie umożliwiają utworzenie nowego układu instalacji w trybie offline, a następnie użyć go, aby zaktualizować swoją kopię programu Visual Studio 2015.

##  <a name="BKMK_tshoot"></a> Rozwiązywanie problemów z instalacją w trybie offline
 Podczas instalacji w trybie offline z trybu offline instalacji pamięci podręcznej, może być wyświetlane komunikaty ostrzegawcze o nie będzie mogła zainstalować niektórych składników i pakietów. Poniższa tabela zawiera możliwe rozwiązania dla tych scenariuszy.


|                                                                                       Składnik lub pakietu                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                                   Rozwiązanie                                                                                                                                                                                                                                                                                                                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Dotfuscator i Analytics Community Edition 5.19.1 (dla wersji Community, Professional i Enterprise programu Visual Studio, zgodnie z zainstalowanym **Windows 7 z dodatkiem SP1** i **systemu Windows Server 2008 R2**) |                                                                                                                                       Jeśli komputer w trybie offline działa **Windows 7 z dodatkiem SP1** lub **systemu Windows Server 2008 R2**, przed zainstalowaniem programu Visual Studio 2015, należy wykonać następujące czynności:<br /><br /> 1.  Konfigurowanie serwera plików lub sieci web do pobierania plików CTL.<br /><br /> 2.    Microsoft automatycznej aktualizacji adres URL przekierowania środowisku bez połączenia.<br /><br /> Aby uzyskać więcej informacji, zobacz [Konfigurowanie zaufanych certyfikatów głównych i niedopuszczalne certyfikaty](https://technet.microsoft.com/library/dn265983.aspx) strony w witrynie Microsoft TechNet.                                                                                                                                       |
|                                                                                  Instalacja zestawu android SDK (poziom interfejsu API)                                                                                   |                                                                        Musi mieć połączenie internetowe, aby zainstalować pakiety zestawu SDK systemu Android (poziom interfejsu API). Jeśli korzystasz z sieci z ograniczeniami, po zainstalowaniu programu Visual Studio muszą zezwalać na dostęp do następujących adresów URL:<br /><br /> -   http://dl.google.com:443<br />-   http://dl-ssl.google.com:443<br />-   https://dl-ssl.google.com/android/repository/*<br /> <br />Aby uzyskać więcej informacji o tym, jak rozwiązać problemy z ustawieniami serwera proxy, zobacz [niepowodzeniami (Instalacja zestawu Android SDK) za serwerem Proxy instalacji programu Visual Studio 2015](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) wpis w blogu.                                                                         |
|                             Szablony elementów rozszerzalności programu Visual Studio<br /><br /> Rozszerzenie GitHub dla programu Visual Studio<br /><br /> Narzędzia programu PowerShell dla programu Visual Studio                             | Jeśli nie masz dostępu do Internetu, po zainstalowaniu programu Visual Studio 2015, można użyć specjalnego Kanał informacyjny offline do generowania układu instalacji w trybie offline. **Uwaga:**  To specjalne źródło danych zawiera najnowsze aktualizacje programu Visual Studio 2015. <br /><br /> Aby utworzyć specjalne Kanał informacyjny offline, uruchom następujące polecenie: / Layout *dysków:* \VisualStudio2015 /overridefeeduri *adres URL do źródła danych xml*<br /><br /> Na przykład język angielski specjalne Kanał informacyjny offline programu Visual Studio 2015 Enterprise, uruchom:<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "http://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Aby uzyskać pełną listę adresów URL, które służy do tworzenia specjalnej Kanał informacyjny offline w wybranym języku zobacz w poniższej tabeli. |

 Użyj następujących adresów URL do utworzenia specyficzny dla języka specjalnego Kanał informacyjny offline, zgodnie z opisem w powyższej tabeli.


|       Język        |                            Adres URL                            |
|-----------------------|-----------------------------------------------------------|
| Chiński uproszczony  | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| Chiński (tradycyjny) | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         czeski         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        niemiecki         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        Angielski        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        Hiszpański        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        Francuski         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        Włoski        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       Japoński        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        koreański         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        polski         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      Portugalski       | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        Rosyjski        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        turecki        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>Zobacz też
 [Instalowanie programu Visual Studio]()