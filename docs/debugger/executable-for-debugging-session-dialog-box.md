---
title: Plik wykonywalny dla sesji, okno dialogowe debugowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41b93ae19afd54b6e22458d1ba12029d5bb93cf3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62849962"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Wykonywalny dla sesji debugowania — Okno dialogowe

To okno dialogowe pojawia się podczas próby debugowania biblioteki DLL dla których nie pliku wykonywalnego jest określony. Program Visual Studio nie można uruchomić biblioteki DLL bezpośrednio. Zamiast tego program Visual Studio uruchamia określony plik wykonywalny. Można debugować biblioteki DLL, gdy jest wywoływana przez plik wykonywalny.

 **Nazwa pliku wykonywalnego** wprowadź nazwę ścieżki do pliku wykonywalnego, który wywołuje bibliotekę DLL debugowania.

 **Adres URL, których projekt może być używane (tylko serwery ATL)** Jeśli debugujesz ATL DLL serwera, wprowadź adres URL gdzie można znaleźć projektu.

 Po wprowadzeniu, te ustawienia są przechowywane w projekcie strony właściwości, dzięki czemu nie trzeba wprowadzać ich ponownie udział podczas kolejnych sesji debugowania. Jeśli potrzebujesz zmienić ustawienia, można otwierać strony właściwości i zmienić wartości. Aby uzyskać więcej informacji na temat określania plik wykonywalny dla sesji debugowania, zobacz [debugowania bibliotek DLL](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Zobacz też

- [Debugowanie w programie Visual Studio](../debugger/index.md)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)