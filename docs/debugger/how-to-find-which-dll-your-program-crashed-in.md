---
title: Znajdź bibliotekę DLL, w której nastąpiła awaria programu | Microsoft Docs
description: Użyj okna moduły, aby określić, która zewnętrzna Biblioteka DLL była aktywna, gdy aplikacja uległa awarii. Można to zrobić dla systemowej biblioteki DLL lub kodu innej osoby.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6eacc8865b3f531df8651ad77d99b319278e6cd1
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903393"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Instrukcje: Znajdowanie biblioteki DLL, w której nastąpiła awaria programu (C#, C++, Visual Basic, F #)

 Jeśli aplikacja ulegnie awarii podczas wywołania do systemowej biblioteki DLL lub kodu innej osoby, należy dowiedzieć się, która Biblioteka DLL była aktywna w przypadku wystąpienia awarii. Jeśli wystąpi awaria w bibliotece DLL poza własnym programem, można zidentyfikować lokalizację przy użyciu okna **moduły** .

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Aby sprawdzić, w którym miejscu wystąpił awaria przy użyciu okna moduły

1. Zanotuj adres, na którym wystąpiła awaria.

    Jeśli adres nie jest wyświetlany w komunikacie o błędzie, może być konieczne użycie alternatywnych metod do identyfikowania biblioteki DLL. Jeśli podejrzewasz, że systemowa biblioteka DLL jest podejrzana, można [załadować symbole](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) z serwerów symboli firmy Microsoft podczas debugowania. W przeciwnym razie może być konieczne [utworzenie pliku zrzutu](../debugger/using-dump-files.md) z informacjami o stercie. Dostępne są różne [Narzędzia](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) do tworzenia plików zrzutu.

2. W menu **Debuguj** wybierz pozycję **Windows**, a następnie kliknij opcję **moduły**.

3. W oknie **moduły** Znajdź kolumnę **adres** . Może być konieczne użycie paska przewijania, aby go zobaczyć.

4. Kliknij przycisk **adresu** w górnej części kolumny, aby posortować biblioteki DLL według adresu.

5. Zeskanuj posortowaną listę, aby znaleźć bibliotekę DLL, której zakres adresów zawiera lokalizację awarii.

6. Przejrzyj kolumny **Nazwa** i **ścieżka** , aby wyświetlić nazwę i ścieżkę biblioteki DLL.

## <a name="see-also"></a>Zobacz też
- [Debugowanie projektów DLL](../debugger/debugging-dll-projects.md)
- [Instrukcje: korzystanie z okna modułów](../debugger/how-to-use-the-modules-window.md)