---
title: 'Instrukcje: Debugowanie natywnych bibliotek DLLs | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65702680"
---
# <a name="how-to-debug-native-dlls"></a>Instrukcje: Debugowanie natywnych bibliotek DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Podczas debugowania biblioteki DLL, należy uruchomić debugowanie od:  
  
- Projekt umożliwiający utworzenie pliku wykonywalnego, który wywołuje bibliotekę DLL.  
  
  \- lub —  
  
- Projekt umożliwiający utworzenie biblioteki DLL, sam.  
  
  Jeśli masz projekt umożliwiający utworzenie pliku wykonywalnego, rozpocząć debugowanie z tego projektu. Następnie można otworzyć pliku źródłowego dla biblioteki DLL i ustawiać punkty przerwania w tym pliku, mimo że nie jest częścią projektu użyty do utworzenia pliku wykonywalnego. Aby uzyskać więcej informacji, zobacz [punktów przerwania](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
  Jeśli uruchomisz debugowanie z projektu, który tworzy bibliotekę DLL, należy określić plik wykonywalny, który chcesz użyć podczas debugowania biblioteki DLL.  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>Aby określić plik wykonywalny dla sesji debugowania  
  
1. W **Eksploratora rozwiązań**, wybierz projekt, który tworzy bibliotekę DLL.  
  
2. Z **widoku** menu, wybierz**stron właściwości**.  
  
3. W **stron właściwości** po otwarciu okna dialogowego **właściwości konfiguracji** i wybierz polecenie **debugowanie** kategorii.  
  
4. W **polecenia** należy określić ścieżkę dla kontenera. Na przykład C:\Program Files\MyApplication\MYAPP. PLIK EXE.  
  
5. W **argumenty wiersza polecenia** wprowadź wszelkie wymagane argumenty dla pliku wykonywalnego.  
  
   Jeśli nie określisz pliku wykonywalnego w _projektu_**stron właściwości** okno dialogowe [pliku wykonywalnego do debugowania sesji okno dialogowe](../debugger/executable-for-debugging-session-dialog-box.md) pojawia się podczas uruchamiania debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)
