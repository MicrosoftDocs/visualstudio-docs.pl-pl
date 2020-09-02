---
title: 'Instrukcje: przełączanie do innego wątku podczas debugowania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f481a0b1cb2142dc7dbfe11e17ac627753cebf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176509"
---
# <a name="how-to-switch-to-another-thread-while-debugging"></a>Porady: przełączanie na inny wątek w trakcie debugowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas debugowania aplikacji wielowątkowej można użyć dowolnej z kilku metod, aby przełączyć kontekst z wątku, z którym pracujesz w innym wątku.  
  
### <a name="to-switch-to-any-thread-that-appears-in-the-threads-window"></a>Aby przełączyć się na dowolny wątek, który pojawia się w oknie wątki  
  
- Kliknij dwukrotnie wątek.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Aby przełączyć się do wątku w oknie źródłowym  
  
- Na lewym marginesie kliknij prawym przyciskiem myszy wskaźnik wątku, wskaż polecenie **Przełącz do**, a następnie kliknij nazwę tego wątku, do którego chcesz się przełączyć. Menu skrótów zawiera tylko wątki w tym konkretnym miejscu.  
  
     Jeśli nie są wyświetlane żadne wskaźniki, kliknij prawym przyciskiem myszy w oknie **wątki** i sprawdź, czy jest zaznaczone pole wyboru **Pokaż wątki w źródle** .  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Aby przełączyć się do wątku na pasku narzędzi lokalizacji debugowania  
  
1. Na pasku narzędzi **Lokalizacja debugowania** kliknij pole **wątek** .  
  
2. Na liście kliknij wątek, do którego chcesz się przełączyć.  
  
## <a name="see-also"></a>Zobacz też  
 [Debuguj wielowątkowe aplikacje](../debugger/debug-multithreaded-applications-in-visual-studio.md)
