---
title: Aplikacje serwera SDI | Microsoft Docs
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
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1296c0f43d0409df0081861095c5ec068932bbc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148145"
---
# <a name="sdi-server-applications"></a>Aplikacje serwera SDI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W przypadku debugowania aplikacji serwera SDI należy określić `/Embedding` lub `/Automation` w właściwości **argumenty wiersza polecenia** w oknie dialogowym strony właściwości *projektu* dla projektów C/C++, C# lub Visual Basic.  
  
 Za pomocą tych argumentów wiersza polecenia debuger może uruchomić aplikację serwera, tak jakby była uruchamiana z kontenera. Uruchomienie kontenera z Menedżera programu lub Menedżera plików spowoduje, że kontener użyje wystąpienia serwera uruchomionego w debugerze.  
  
## <a name="finding-the-command-line-arguments-property"></a>Znajdowanie Właściwości argumentów wiersza polecenia  
 Aby uzyskać dostęp do okna dialogowego strony właściwości *projektu* , kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań, a następnie wybierz polecenie Właściwości z menu skrótów. Aby znaleźć Właściwość argumenty wiersza polecenia, rozwiń kategorię właściwości konfiguracji i kliknij stronę debugowanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie modelu COM i ActiveX](../debugger/com-and-activex-debugging.md)   
 [Instrukcje: debugowanie serwerów COM](../debugger/how-to-debug-com-servers.md)
