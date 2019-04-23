---
title: 'Instrukcje: Informacje o symbolach Windows odwołania | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 45e1ad3c89d811a0a2bd715c86d8fcd8006600b0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60086705"
---
# <a name="how-to-reference-windows-symbol-information"></a>Instrukcje: Informacje o symbolach Windows odwołania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Profiling Tools umożliwia rozpoznawanie nazw symbolicznych takich jak nazwy funkcji w plikach binarnych program plików symboli (.pdb). Można wykonaj następujące kroki, aby automatycznie Pobierz i zaktualizuj pliki .pdb poprawne dla wersji systemu Windows na komputerze lokalnym.  
  
> [!NOTE]
>  To ustawienie nie wpływa na istniejące raporty. Tylko raporty utworzone po określeniu serwera symboli będzie mieć informacji o symbolach.  
  
 Aby uzyskać więcej informacji, zobacz [Określ symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### <a name="to-use-the-microsoft-symbol-server"></a>Aby użyć serwera symboli firmy Microsoft  
  
1. Tworzenie folderu zawierającego plik informacje o symbolach, takich jak C:\SymbolCache.  
  
2. Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
     **Opcje** pojawi się okno dialogowe.  
  
3. Rozwiń **debugowanie** drzewa, a następnie kliknij przycisk **symbole**.  
  
4. W **symboli (.pdb) lokalizacji**, wybierz opcję **serwery symboli firmy Microsoft**  
  
5. W **Buforuj symbole z serwera symboli do tego katalogu**, wpisz ścieżkę do folderu, który został utworzony w kroku 1, na przykład:  
  
     **C:\SymbolCache**  
  
     Możesz również kliknąć przycisk wielokropka (**...** ) a następnie wybierz katalog, z **przeglądanie w poszukiwaniu folderu** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Instrukcje: Serializacja informacji o symbolach](../profiling/how-to-serialize-symbol-information.md)
