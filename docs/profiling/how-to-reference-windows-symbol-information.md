---
title: Informacje o symbolach systemu Windows Microsoft Docs
description: Dowiedz się, w jaki sposób program Visual Studio narzędzia profilowania używać plików symboli (. pdb) do rozpoznawania symbolicznych nazw, takich jak nazwy funkcji w plikach binarnych programu.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c788be648b77a36b8da7027c89a7d9cb047b57d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907094"
---
# <a name="how-to-reference-windows-symbol-information"></a>Instrukcje: odwołania do informacji o symbolach w systemie Windows
Program Visual Studio narzędzia profilowania używać symbolu (.*PDB*) do rozpoznawania nazw symbolicznych, takich jak nazwy funkcji w plikach binarnych programu. Możesz wykonać następujące kroki, aby automatycznie pobrać i zaktualizować poprawną. pliki *PDB* dla wersji systemu Windows na komputerze lokalnym.

> [!NOTE]
> To ustawienie nie ma wpływu na istniejące raporty. Tylko raporty utworzone po określeniu serwera symboli będą miały informacje o symbolach.

 Aby uzyskać więcej informacji, zobacz [Określanie symbolu (.*PDB*) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-use-the-microsoft-symbol-server"></a>Aby użyć serwera symboli firmy Microsoft

1. Utwórz folder, który będzie zawierać informacje o pliku symboli, takie jak C:\SymbolCache.

2. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).

     Zostanie wyświetlone okno dialogowe **Opcje** .

3. Rozwiń drzewo **debugowanie** , a następnie kliknij pozycję **symbole**.

4. W **lokalizacjach pliku symboli (. pdb)** wybierz pozycję **serwery symboli Microsoft**

5. W polu **symbole pamięci podręcznej z serwera symboli do tego katalogu** wpisz ścieżkę do folderu, który został utworzony w kroku 1, na przykład:

     **C:\SymbolCache**

     Możesz również kliknąć przycisk wielokropka (**...**), a następnie wybrać katalog z okna dialogowego **Przeglądaj w poszukiwaniu folderu** .

## <a name="see-also"></a>Zobacz też
- [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
- [Instrukcje: Serializowanie informacji o symbolach](../profiling/how-to-serialize-symbol-information.md)
