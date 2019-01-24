---
title: Wdrażanie powłoki VS Shell | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6c79a8a0558594e8981959750ebd348b6f9f4d60
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54773454"
---
# <a name="vs-shell-deployment"></a>Wdrażanie powłoki VS Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Powłoka w trybie izolowanym pozwala określić, które program Visual Studio funkcji należy korzystać z języka specyficznego dla domeny i wygląd tego rozwiązania. Aby uzyskać więcej informacji na temat powłoki programu Visual Studio, izolowany zobacz [Dostosowywanie programu Isolated Shell](../extensibility/customizing-the-isolated-shell.md). Można znaleźć więcej informacji na temat sposobu dostosowywania programu isolated shell w [Dostosowywanie programu Isolated Shell](http://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Aby ustawić Visual Studio Shell jako cel wdrożenia  
  
1.  W **DslPackage** otwarty projekt **source.extension.tt**.  
  
2.  W obszarze `<SupportedProducts>` Wstaw:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Zastąp *MyIsolatedShell* o nazwie pakietu shell w trybie izolowanym.
