---
title: Właściwości sesji wydajności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
ms.assetid: c3a86913-172b-488f-a31a-cea01a71b2ea
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed020d09bc3c7b85a395625f410f0062bf4bfac9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739276"
---
# <a name="performance-session-properties"></a>Właściwości sesji wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A **sesji wydajności** umożliwia skonfigurowanie ustawień, które określają, jak jest profilowana aplikacja. Przechowuje także raporty, które są generowane dla sesji profilowania.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Możesz utworzyć **sesji wydajności** , uruchamiając **kreatora wydajności** lub za pomocą ręcznego tworzenia sesji. **Sesji wydajności** jest wyświetlany w **Eksplorator wydajności** po **sesji wydajności** została utworzona.  
  
  Aby wyświetlić **sesji wydajności** właściwości, wybierz nazwę sesji, w **Eksplorator wydajności**, kliknij go prawym przyciskiem myszy, a następnie wybierz **właściwości**.  
  
  Sesja wydajności ma następujące strony właściwości:  
  
## <a name="general"></a>Ogólne  
 Te ustawienia umożliwiają wybór metody, można dodać kolekcji obiektów .NET i danych o okresie istnienia, aby określić domyślną lokalizację raportu profilowania i nazewnictwa konwencje.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
 [Instrukcje: wybieranie metod zbierania](../profiling/how-to-choose-collection-methods.md)  
  
 [Zbieranie danych alokacji pamięci .NET i okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
 [Instrukcje: ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)  
  
## <a name="launch"></a>Uruchom  
 Te ustawienia pozwalają na wybranie z listy plików binarnych, a także określić kolejność uruchamiania plików binarnych.  
  
 Aby uzyskać więcej informacji, zobacz [porady: Określanie plików binarnych do ekranu startowego](../profiling/how-to-specify-the-binary-to-start.md)  
  
## <a name="sampling"></a>Próbkowania  
 Te ustawienia umożliwiają wybierz interwał próbkowania zdarzeń i próbkowania, podczas próbkowania jest używana jako metoda profilowania. Zdarzenie próbkowania służy do zbierania danych profilowania w określonym interwale. Na przykład, jeśli zdarzenie próbkowania cykli zegara, a interwał próbkowania jest ustawiony na 10 000 000, następnie danych profilowania są zbierane po co 10 milionów cykli zegara. Dostępne są następujące cztery przykładowe zdarzenia:  
  
- Cykle zegara - procesora CPU związane problemy  
  
- Problemy związane z błędów stron — pamięci  
  
- System wywołuje — dla operacji We/Wy problemy związane z  
  
- Liczniki wydajności — problemy z wydajnością niskiego poziomu  
  
- Przykładowe dodatkowe zdarzenia może być określony w oparciu o dostępne liczniki wydajności  
  
  Aby uzyskać więcej informacji, zobacz [porady: Wybieranie zdarzeń pobierania próbek](../profiling/how-to-choose-sampling-events.md)  
  
## <a name="binary"></a>plików binarnych  
 Te ustawienia umożliwiają określenie, czy chcesz przenieść instrumentowanego pliku binarnego do innej lokalizacji. Na przykład jeśli profilowany My.DLL i nie chcesz zmienić lokalizację instrumentowanych danych binarnych, utworzyć kopię zapasową o nazwie My.Orig.DLL My.DLL powstaje. Następnie My.DLL jest modyfikowany przez wstawienie sondy do zbierania danych. Jeśli zdecydujesz się zmienić lokalizację instrumentowanych danych binarnych, oryginalny plik binarny nie została zmieniona i instrumentowanego pliku binarnego jest kopiowany do określonej lokalizacji do użycia podczas instrumentacji.  
  
 Aby uzyskać więcej informacji, zobacz [porady: Określanie plików binarnych do ekranu startowego](../profiling/how-to-specify-the-binary-to-start.md)  
  
## <a name="tier-interactions"></a>Interakcje warstw  
 Aby uzyskać więcej informacji, zobacz [zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)  
  
## <a name="instrumentation"></a>Oprzyrządowanie  
 Te ustawienia umożliwiają zbieranie danych dotyczących wydajności dla kodu języka JScript w [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] strony sieci Web i określ opcje **przed Instrumentacją** i **po Instrumentacji** zdarzenia, które ma być wykonywana przed lub po nim proces instrumentacji.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
 [Instrukcje: profilowanie kodu JavaScript na stronach internetowych](../profiling/how-to-profile-javascript-code-in-web-pages.md)  
  
 [Instrukcje: określanie poleceń przed i po instrumentacji](../profiling/how-to-specify-pre-and-post-instrument-commands.md)  
  
## <a name="cpu-counters"></a>Liczniki procesora CPU  
 Te ustawienia umożliwiają zbieranie danych dotyczących liczników wydajności procesora CPU, gdy używana jest metoda profilowania instrumentacji. Przenośne liczniki wydajności są dostępne niezależnie od tego, czy projekt procesora CPU lub producentem. Zdarzenia platformy są specyficzne dla projektu procesora CPU i producenta. Więcej informacji na temat liczników wydajności na układ znajduje się w dokumentacji określony procesor.  
  
 Aby uzyskać więcej informacji, zobacz [porady: zbieranie danych licznika procesora CPU](../profiling/how-to-collect-cpu-counter-data.md)  
  
## <a name="windows-events"></a>Zdarzenia Windows  
 Podczas profilowania, umożliwia zbieranie danych z dostawców śledzenia zdarzeń. Dane można wyświetlić za pomocą narzędzia wiersza polecenia VSPerfReport.exe `/calltrace` opcji. Aby uzyskać więcej informacji na temat śledzenie zdarzeń dla Windows (ETW), zobacz [temat śledzenia zdarzeń](http://go.microsoft.com/fwlink/?linkid=90752).  
  
 Aby uzyskać więcej informacji, zobacz:  
  
 [Instrukcje: zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)  
  
 [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="windows-counters"></a>Liczniki Windows  
 Ta opcja umożliwia zbieranie danych z liczników monitora wydajności Windows. Aby zbierać dane, zaznacz pole wyboru przy opcji **zbierania liczników wydajności Windows**. Interwał zbierania można ustawić w **interwał zbierania** pole. **Kategoria licznika** i **wystąpienia** mogą być również dostępne. Niektóre domyślne liczniki Monitora wydajności Windows są dostępne.  
  
 Aby uzyskać więcej informacji, zobacz [porady: zbieranie danych licznika Windows](../profiling/how-to-collect-windows-counter-data.md).  
  
## <a name="advanced"></a>Zaawansowane  
 Te ustawienia umożliwiają dodawanie opcji do procesu instrumentacji, określając jeden lub więcej opcji [VSInstr](../profiling/vsinstr.md) wiersza polecenia narzędzia profilowania. Jeśli aplikacja korzysta z więcej niż jedna wersja, można również określić wersję środowiska uruchomieniowego wspólnego profilu.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
 [Instrukcje: określanie środowiska uruchomieniowego programu .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)  
  
 [Instrukcje: określanie dodatkowych opcji instrumentacji](../profiling/how-to-specify-additional-instrumentation-options.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../profiling/overviews-performance-tools.md)   
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)



