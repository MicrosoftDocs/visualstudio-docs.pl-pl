---
title: Plik wykonywalny dla sesji debugowania — okno dialogowe | Microsoft Docs
description: Aby debugować bibliotekę DLL, należy określić plik wykonywalny do wywołania biblioteki DLL. Dowiedz się więcej o oknie dialogowym, które pojawia się, gdy nie określono pliku wykonywalnego.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 20f97c7597dc266fbb4334daf27d3660b351f35a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870834"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Wykonywalny dla sesji debugowania — Okno dialogowe

To okno dialogowe jest wyświetlane podczas próby debugowania biblioteki DLL, dla której nie został określony plik wykonywalny. Program Visual Studio nie może bezpośrednio uruchomić biblioteki DLL. Zamiast tego program Visual Studio uruchamia określony plik wykonywalny. Można debugować bibliotekę DLL, gdy jest wywoływana przez plik wykonywalny.

 **Nazwa pliku wykonywalnego** Wprowadź nazwę ścieżki do pliku wykonywalnego, który wywołuje debugowaną bibliotekę DLL.

 **Adres URL, do którego można uzyskać dostęp do projektu (tylko serwer ATL)** W przypadku debugowania biblioteki DLL serwera ATL wprowadź adres URL, pod którym można znaleźć projekt.

 Po wprowadzeniu tych ustawień te ustawienia są przechowywane na stronach właściwości projektu, więc nie trzeba wprowadzać ich ponownie w przypadku kolejnych sesji debugowania. Jeśli trzeba zmienić ustawienia, można otworzyć strony właściwości i zmienić wartości. Aby uzyskać więcej informacji na temat określania pliku wykonywalnego dla sesji debugowania, zobacz [debugowanie bibliotek DLL](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Zobacz też

- [Debugowanie w Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)