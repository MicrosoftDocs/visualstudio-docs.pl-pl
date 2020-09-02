---
title: Pliki źródłowe debugowania, wspólne właściwości, okno dialogowe strony właściwości rozwiązania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 47fb2511e39153753a2c27483dd6ac96c26c9e83
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143029"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Debugowanie plików źródłowych, typowe właściwości, strony właściwości rozwiązania — Okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta strona właściwości określa, gdzie debuger ma szukać plików źródłowych podczas debugowania rozwiązania.  
  
 Aby uzyskać dostęp do strony właściwości **pliki źródłowe debugowania** , kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości** z menu skrótów. Rozwiń folder **wspólne właściwości** , a następnie kliknij stronę **debugowanie plików źródłowych** .  
  
 **Katalogi zawierające kod źródłowy**  
 Zawiera listę katalogów, w których debuger wyszukuje pliki źródłowe podczas debugowania rozwiązania. Podkatalogi określonych katalogów są również przeszukiwane.  
  
 **Nie wyszukuj tych plików źródłowych**  
 Wprowadź nazwy wszystkich plików, które nie mają być odczytywane przez debuger. Jeśli debuger odnajdzie jeden z tych plików w jednym z katalogów określonych powyżej, zostanie on zignorowany. Jeśli okno dialogowe **Znajdowanie źródła** pojawia się w trakcie debugowania i klikniesz przycisk **Anuluj**, wyszukiwany plik zostanie dodany do tej listy, dzięki czemu debuger nie będzie kontynuował wyszukiwania tego pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
