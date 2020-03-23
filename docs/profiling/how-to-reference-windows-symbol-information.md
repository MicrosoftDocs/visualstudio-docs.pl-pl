---
title: 'Jak: Odwoływanie się do informacji o symbolach systemu Windows | Dokumenty firmy Microsoft'
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 28bbd4b584d679c03c58ba8532ced3f28f16d6aa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774916"
---
# <a name="how-to-reference-windows-symbol-information"></a>Instrukcje: odwołania do informacji o symbolach w systemie Windows
Narzędzia do profilowania programu Visual Studio używają symbolu (.* pdb)* do rozpoznawania nazw symbolicznych, takich jak nazwy funkcji w plikach binarnych programu. Możesz wykonać następujące kroki, aby automatycznie pobrać i zaktualizować poprawny plik . *pliki pdb* dla wersji systemu Windows na komputerze lokalnym.

> [!NOTE]
> To ustawienie nie ma wpływu na istniejące raporty. Tylko raporty utworzone po określeniu serwera symboli będą miały informacje o symbolu.

 Aby uzyskać więcej informacji, zobacz [Określanie symbolu (.* pdb*) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-use-the-microsoft-symbol-server"></a>Aby użyć serwera symboli firmy Microsoft

1. Utwórz folder zawierający informacje o pliku symbolu, takie jak C:\SymbolCache.

2. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).

     Zostanie wyświetlone okno dialogowe **Opcje.**

3. Rozwiń drzewo **debugowania,** a następnie kliknij pozycję **Symbole**.

4. W **lokalizacjach pliku symbolu (pdb)** wybierz pozycję **Serwery symboli firmy Microsoft**

5. W **symbolach pamięci podręcznej z serwera symboli do tego katalogu**wpisz ścieżkę folderu utworzonego w kroku 1, na przykład:

     **C:\Skrzynka z symbolami**

     Można również kliknąć przycisk wielokropka (**...**), a następnie wybrać katalog z okna dialogowego **Przeglądaj folder.**

## <a name="see-also"></a>Zobacz też
- [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
- [Jak: Serialize informacje o symbolu](../profiling/how-to-serialize-symbol-information.md)
