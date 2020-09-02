---
title: Plik wykonywalny dla sesji debugowania — okno dialogowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c2ee71c5e23b0c5784cd2fe9b57b46fe28d41d30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157469"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Wykonywalny dla sesji debugowania — Okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To okno dialogowe jest wyświetlane podczas próby debugowania biblioteki DLL, dla której nie został określony plik wykonywalny. Program Visual Studio nie może bezpośrednio uruchomić biblioteki DLL. Zamiast tego zostanie uruchomiony określony plik wykonywalny. Można debugować bibliotekę DLL, gdy jest wywoływana przez plik wykonywalny.  
  
 **Nazwa pliku wykonywalnego**  
 Wprowadź nazwę ścieżki do pliku wykonywalnego, który wywołuje debugowaną bibliotekę DLL.  
  
 **Adres URL, do którego można uzyskać dostęp do projektu (tylko serwer ATL)**  
 W przypadku debugowania biblioteki DLL serwera ATL wprowadź adres URL, pod którym można znaleźć projekt.  
  
 Po wprowadzeniu tych ustawień te ustawienia są przechowywane na stronach właściwości projektu, więc nie trzeba wprowadzać ich ponownie w przypadku kolejnych sesji debugowania. Jeśli trzeba zmienić ustawienia, można otworzyć strony właściwości i zmienić wartości. Aby uzyskać więcej informacji na temat określania pliku wykonywalnego dla sesji debugowania, zobacz [debugowanie bibliotek DLL](../debugger/how-to-debug-native-dlls.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w Visual Studio](../debugger/debugging-in-visual-studio.md)
