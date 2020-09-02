---
title: 'Instrukcje: wyłączanie procesu hostingu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95dcd7da113bfe996d00e617b7c8e2f9b68864d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667972"
---
# <a name="how-to-disable-the-hosting-process"></a>Porady: wyłączanie procesu hostingu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na wywołania niektórych interfejsów API mogą być narażone zmiany, gdy proces hostingu jest włączony. W takich przypadkach należy wyłączyć proces hostingu, aby zwracał poprawne wyniki.

### <a name="to-disable-the-hosting-process"></a>Aby wyłączyć proces hostingu

1. Otwórz projekt wykonywalny w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Dla projektów, które nie generują plików wykonywalnych (na przykład biblioteki klas lub projektów usług), nie można korzystać z tej opcji.

2. W menu **projekt** kliknij polecenie **Właściwości**.

3. Kliknij kartę **debugowanie** .

4. Wyczyść pole wyboru **Włącz proces hostingu programu Visual Studio** .

   Gdy proces hostingu jest wyłączony, niektóre funkcje debugowania są niedostępne lub zmniejszają wydajność. Aby uzyskać więcej informacji, zobacz [debugowanie i proces hostingu](../debugger/debugging-and-the-hosting-process.md).

   Ogólnie rzecz biorąc, gdy proces hostingu jest wyłączony:

- Czas wymagany do rozpoczęcia debugowania [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] aplikacji.

- Ocena wyrażenia czasu projektowania jest niedostępna.

- Debugowanie częściowej relacji zaufania jest niedostępne.

## <a name="see-also"></a>Zobacz też
 [Debugowanie i](../debugger/debugging-and-the-hosting-process.md) proces hostingu procesów hostingu [(vshost.exe)](../ide/hosting-process-vshost-exe.md) [kompilacji podczas tworzenia aplikacji](https://msdn.microsoft.com/c9497d62-3b7b-4449-88e8-cf27acc9efe6)
