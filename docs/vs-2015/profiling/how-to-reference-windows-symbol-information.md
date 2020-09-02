---
title: 'Instrukcje: odwołania do informacji o symbolach systemu Windows | Microsoft Docs'
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
ms.openlocfilehash: c7a123a42c1a46faf67fb5b63b1ab4ef300735f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64822699"
---
# <a name="how-to-reference-windows-symbol-information"></a>Porady: odwołania do informacji o symbolach w systemie Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio narzędzia profilowania używać plików symboli (. pdb) do rozpoznawania symbolicznych nazw, takich jak nazwy funkcji w plikach binarnych programu. Możesz wykonać następujące kroki, aby automatycznie pobrać i zaktualizować poprawne pliki. pdb dla wersji systemu Windows na komputerze lokalnym.  
  
> [!NOTE]
> To ustawienie nie ma wpływu na istniejące raporty. Tylko raporty utworzone po określeniu serwera symboli będą miały informacje o symbolach.  
  
 Aby uzyskać więcej informacji, zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### <a name="to-use-the-microsoft-symbol-server"></a>Aby użyć serwera symboli firmy Microsoft  
  
1. Utwórz folder, który będzie zawierać informacje o pliku symboli, takie jak C:\SymbolCache.  
  
2. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).  
  
     Zostanie wyświetlone okno dialogowe **Opcje** .  
  
3. Rozwiń drzewo **debugowanie** , a następnie kliknij pozycję **symbole**.  
  
4. W **lokalizacjach pliku symboli (. pdb)** wybierz pozycję **serwery symboli Microsoft**  
  
5. W polu **symbole pamięci podręcznej z serwera symboli do tego katalogu**wpisz ścieżkę do folderu, który został utworzony w kroku 1, na przykład:  
  
     **C:\SymbolCache**  
  
     Możesz również kliknąć przycisk wielokropka (**...**), a następnie wybrać katalog z okna dialogowego **Przeglądaj w poszukiwaniu folderu** .  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Instrukcje: serializacja informacji o symbolach](../profiling/how-to-serialize-symbol-information.md)
