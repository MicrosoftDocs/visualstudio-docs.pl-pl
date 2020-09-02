---
title: 'Instrukcje: debugowanie natywnych bibliotek DLL | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- DLLs, debugging
- executable files, specifying for debug sessions
ms.assetid: 76b34d15-a66d-4963-842e-c8b955c81696
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 16a533b27e619526edab71374d922e68baf0a4b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702680"
---
# <a name="how-to-debug-native-dlls"></a>Porady: Debugowanie natywnych bibliotek DLLs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Podczas debugowania biblioteki DLL można rozpocząć debugowanie z:  
  
- Projekt użyty do utworzenia pliku wykonywalnego, który wywołuje bibliotekę DLL.  
  
  \- oraz  
  
- Projekt używany do utworzenia samej biblioteki DLL.  
  
  Jeśli masz projekt użyty do utworzenia pliku wykonywalnego, Rozpocznij debugowanie z tego projektu. Następnie można otworzyć plik źródłowy dla biblioteki DLL i ustawić punkty przerwania w tym pliku, nawet jeśli nie jest on częścią projektu użytego do utworzenia pliku wykonywalnego. Aby uzyskać więcej informacji, zobacz [punkty przerwania](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
  Jeśli zaczniesz debugowanie z projektu, który tworzy bibliotekę DLL, musisz określić plik wykonywalny, który ma być używany w debugowaniu biblioteki DLL.  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>Aby określić plik wykonywalny dla sesji debugowania  
  
1. W **Eksplorator rozwiązań**wybierz projekt, który tworzy bibliotekę DLL.  
  
2. Z menu **Widok** wybierz polecenie**strony właściwości**.  
  
3. W oknie dialogowym **strony właściwości** Otwórz folder **Właściwości konfiguracji** i wybierz kategorię **debugowanie** .  
  
4. W polu **polecenie** Określ nazwę ścieżki dla kontenera. Na przykład C:\Program Files\MyApplication\MYAPP.EXE.  
  
5. W polu **argumenty polecenia** określ wszelkie wymagane argumenty dla pliku wykonywalnego.  
  
   Jeśli nie określisz pliku wykonywalnego w oknie dialogowym**strony właściwości** _projektu_, podczas uruchamiania debugowania zostanie wyświetlone okno [dialogowe plik wykonywalny dla sesji debugowania](../debugger/executable-for-debugging-session-dialog-box.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie w Visual Studio](../debugger/debugging-in-visual-studio.md)
