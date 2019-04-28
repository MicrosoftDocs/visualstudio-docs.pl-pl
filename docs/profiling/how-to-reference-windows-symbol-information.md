---
title: 'Instrukcje: Informacje o symbolach Windows odwołania | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91b5c90b2451780458982ba73a0e04672fa2e507
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422870"
---
# <a name="how-to-reference-windows-symbol-information"></a>Instrukcje: Odwołania do informacji o symbolach w systemie Windows
Visual Studio Profiling Tools należy użyć symbolu (. *plik PDB*) pliki do rozpoznawania nazw symbolicznych, takich jak nazwy funkcji w pliki binarne programu. Można wykonaj następujące kroki, próbę automatycznego pobrania i aktualizacji poprawny. *pdb* plików dla wersji systemu Windows na komputerze lokalnym.

> [!NOTE]
> To ustawienie nie wpływa na istniejące raporty. Tylko raporty utworzone po określeniu serwera symboli będzie mieć informacji o symbolach.

 Aby uzyskać więcej informacji, zobacz [Określ symbol (. *plik PDB*) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-use-the-microsoft-symbol-server"></a>Aby użyć serwera symboli firmy Microsoft

1. Tworzenie folderu zawierającego plik informacje o symbolach, takich jak C:\SymbolCache.

2. Na **narzędzia** menu, kliknij przycisk **opcje**.

     **Opcje** pojawi się okno dialogowe.

3. Rozwiń **debugowanie** drzewa, a następnie kliknij przycisk **symbole**.

4. W **symboli (.pdb) lokalizacji**, wybierz opcję **serwery symboli firmy Microsoft**

5. W **Buforuj symbole z serwera symboli do tego katalogu**, wpisz ścieżkę do folderu, który został utworzony w kroku 1, na przykład:

     **C:\SymbolCache**

     Możesz również kliknąć przycisk wielokropka (**...** ) a następnie wybierz katalog, z **przeglądanie w poszukiwaniu folderu** okno dialogowe.

## <a name="see-also"></a>Zobacz także
- [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
- [Instrukcje: Serializacja informacji o symbolach](../profiling/how-to-serialize-symbol-information.md)