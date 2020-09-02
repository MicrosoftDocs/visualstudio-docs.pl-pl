---
title: 'Instrukcje: debugowanie kontrolki ActiveX | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.controls.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9524ab08ab955609f29f437e8a1576af02738aa1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704462"
---
# <a name="how-to-debug-an-activex-control"></a>Porady: debugowanie formantu ActiveX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

KORYGUJĄC
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Aby debugować formant ActiveX, należy określić kontener (plik wykonywalny), w którym ma zostać uruchomiony formant.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Aby określić kontener dla sesji debugowania  
  
1. W Eksplorator rozwiązań wybierz projekt.  
  
2. Z menu **Widok** wybierz polecenie **strony właściwości**.  
  
3. W oknie dialogowym **strony właściwości projektu** Otwórz folder **Właściwości konfiguracji** , a następnie wybierz pozycję **debugowanie**.  
  
4. W kategorii **debugowanie** Znajdź właściwość **polecenie** .  
  
5. Określ nazwę ścieżki dla kontenera. Na przykład C:\Program Files\Internet Explorer\IEXPLORE.EXE.  
  
6. W przypadku określenia programu Internet Explorer jako kontenera i używania programu Active Desktop wpisz `/new` w polu **argumenty polecenia** .  
  
7. Kliknij przycisk **OK**.  
  
     Jeśli nie określisz kontenera w oknie dialogowym **strony właściwości projektu** , możesz określić kontener po rozpoczęciu debugowania. Po wybraniu polecenia wykonywania w celu rozpoczęcia debugowania zostanie wyświetlone okno [dialogowe plik wykonywalny dla sesji debugowania](../debugger/executable-for-debugging-session-dialog-box.md) . Określ nazwę ścieżki kontenera w oknie dialogowym.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX](https://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [Testowanie właściwości i zdarzeń za pomocą kontenera testów](https://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [Debugowanie modelu COM i ActiveX](../debugger/com-and-activex-debugging.md)   
 [Debugowanie w Visual Studio](../debugger/debugging-in-visual-studio.md)
