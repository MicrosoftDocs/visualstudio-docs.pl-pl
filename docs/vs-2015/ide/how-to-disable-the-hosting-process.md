---
title: 'Instrukcje: Wyłączanie procesu hostingu | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0266e14b3a03e6d8225e7ec9283fe727a9502e53
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785884"
---
# <a name="how-to-disable-the-hosting-process"></a>Instrukcje: Wyłączanie procesu hostingu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wywołania niektórych interfejsów API mogą mieć wpływ na włączenie procesu hostingu. W takich przypadkach zachodzi konieczność wyłączanie procesu hostingu, aby zwracać poprawnych wyników.  
  
### <a name="to-disable-the-hosting-process"></a>Aby wyłączyć procesu hostingu  
  
1. Otwórz projekt wykonywalny w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Projekty, które nie tworzą pliki wykonywalne (na przykład klasy biblioteki lub usługi projektów) nie ma takiej możliwości.  
  
2. Na **projektu** menu, kliknij przycisk **właściwości**.  
  
3. Kliknij przycisk **debugowania** kartę.  
  
4. Wyczyść **włączyć procesu hostingu Visual Studio** pole wyboru.  
  
   Po wyłączeniu procesu hostingu kilka funkcji debugowania są niedostępne lub wystąpić obniżenie wydajności. Aby uzyskać więcej informacji, zobacz [debugowanie i proces hostingu](../debugger/debugging-and-the-hosting-process.md).  
  
   Ogólnie rzecz biorąc, gdy proces hostingu jest wyłączony:  
  
-   Czas potrzebny, aby rozpocząć debugowanie [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zwiększa aplikacji.  
  
-   Obliczanie wyrażenia czasu projektowania jest niedostępny.  
  
-   Debugowanie w częściowej relacji zaufania jest niedostępny.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie i proces hostingu](../debugger/debugging-and-the-hosting-process.md)   
 [Proces hostingu (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Kompilacje podczas tworzenia aplikacji](http://msdn.microsoft.com/c9497d62-3b7b-4449-88e8-cf27acc9efe6)
