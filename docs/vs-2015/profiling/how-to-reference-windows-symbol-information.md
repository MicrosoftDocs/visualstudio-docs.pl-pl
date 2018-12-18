---
title: 'Porady: odwoływać się do informacji o symbolach Windows | Dokumentacja firmy Microsoft'
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
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c18825a27bfefdd1a6c817951983d85ac459b78b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763594"
---
# <a name="how-to-reference-windows-symbol-information"></a>Porady: odwołania do informacji o symbolach w systemie Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Profiling Tools umożliwia rozpoznawanie nazw symbolicznych takich jak nazwy funkcji w plikach binarnych program plików symboli (.pdb). Można wykonaj następujące kroki, aby automatycznie Pobierz i zaktualizuj pliki .pdb poprawne dla wersji systemu Windows na komputerze lokalnym.  
  
> [!NOTE]
>  To ustawienie nie wpływa na istniejące raporty. Tylko raporty utworzone po określeniu serwera symboli będzie mieć informacji o symbolach.  
  
 Aby uzyskać więcej informacji, zobacz [Określ symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### <a name="to-use-the-microsoft-symbol-server"></a>Aby użyć serwera symboli firmy Microsoft  
  
1.  Tworzenie folderu zawierającego plik informacje o symbolach, takich jak C:\SymbolCache.  
  
2.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
     **Opcje** pojawi się okno dialogowe.  
  
3.  Rozwiń **debugowanie** drzewa, a następnie kliknij przycisk **symbole**.  
  
4.  W **symboli (.pdb) lokalizacji**, wybierz opcję **serwery symboli firmy Microsoft**  
  
5.  W **Buforuj symbole z serwera symboli do tego katalogu**, wpisz ścieżkę do folderu, który został utworzony w kroku 1, na przykład:  
  
     **C:\SymbolCache**  
  
     Możesz również kliknąć przycisk wielokropka (**...** ) a następnie wybierz katalog, z **przeglądanie w poszukiwaniu folderu** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Instrukcje: serializacja informacji o symbolach](../profiling/how-to-serialize-symbol-information.md)



