---
title: 'Porady: Odnajdywanie DLL, która nastąpiła awaria programu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40f27e0bec20e1dd037beaa5f60ea648c0ccb171
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257100"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Porady: Odnajdywanie DLL, która nastąpiła awaria programu (C#, C++, Visual Basic F#)
  
 Jeśli aplikacja ulegnie awarii podczas wywoływania biblioteki DLL systemu lub innej osoby kodu, musisz znaleźć się, które biblioteki DLL była aktywna podczas wystąpienia awarii. Jeśli wystąpi awaria w bibliotece DLL poza własny program, można zidentyfikować lokalizację za pomocą **modułów** okna.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Aby dowiedzieć się, w przypadku, gdy awaria wystąpił podczas korzystania z okna modułów  
  
1.  Zanotuj adres, w których wystąpiła awaria.

    Jeśli adres nie jest wyświetlany komunikat o błędzie, może być konieczne Zidentyfikuj bibliotekę DLL przy użyciu alternatywnych metod. Jeśli podejrzewasz systemowej biblioteki DLL, możesz to zrobić [załadować symbole](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) z serwerów symboli firmy Microsoft, podczas debugowania. W przeciwnym razie konieczne może być [Tworzenie pliku zrzutu](../debugger/using-dump-files.md) przy użyciu sterty informacji w zamian. Różne [narzędzia](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) są dostępne do tworzenia plików zrzutu.
  
2.  Na **debugowania** menu, wybierz **Windows**i kliknij przycisk **modułów**.  
  
3.  W **modułów** oknie Znajdź **adres** kolumny. Może być konieczne sprawdzenie za pomocą paska przewijania.  
  
4.  Kliknij przycisk **adres** przycisku w górnej części kolumny, aby sortować biblioteki DLL przy użyciu adresu.  
  
5.  Skanowanie posortowaną listę można znaleźć biblioteki DLL, którego zakres adresów zawiera lokalizację awarii.  
  
6.  Przyjrzyj się **nazwa** i **ścieżki** kolumny, aby wyświetlić nazwę biblioteki DLL i ścieżkę.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie projektów DLL](../debugger/debugging-dll-projects.md)   
 [Instrukcje: korzystanie z okna modułów](../debugger/how-to-use-the-modules-window.md)