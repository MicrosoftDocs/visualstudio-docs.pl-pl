---
title: Omówienie modelu automatyzacji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65698c140647831ab329069e61e2cc5ea826d6e5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992116"
---
# <a name="automation-model-overview"></a>Omówienie modelu automatyzacji
Model automatyzacji zawiera zestaw obiektów, wobec których można napisać dodatek programu Visual Studio lub rozszerzenia. Dodatek jest aplikacja, która może manipulować środowiska Visual Studio i automatyzacji typowych zadań. Rozszerzenia programu Visual Studio można tworzyć niestandardowe składniki programu Visual Studio lub dodać do funkcji składniki standardowe, takich jak edytor tekstu.  
  
## <a name="objects-in-the-automation-model"></a>Obiekty w modelu automatyzacji  
 Model automatyzacji składa się z powiązanych grup obiektów, które kontrolują główne aspekty wspólnego środowiska. Na poniższym diagramie przedstawiono obszerny zestaw obiektów programu Visual Studio, które tworzą model automatyzacji.  
  
 ![Visual Studio automation object chart](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
  
 Aby uzyskać więcej informacji, zobacz [rozszerzanie środowiska Visual Studio](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 Środowisko udostępnia model dla różnych obszarów funkcjonalnych. Na przykład jest model kodu dla różnych elementów, które mogą być w kodzie. Brak model dokumentu do różnych elementów dokumentu. Jeden obszar, obszar projektu jest szczególne znaczenie w odniesieniu do dostawców pakietu VSPackage. Prawdopodobnie będziesz nowych typów projektów, aby współtworzyć modelu automatyzacji w podobny sposób jak [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Współtworzenie modelu automatyzacji. Czy proces jest opisany w [zapewnianie automatyzacji pakietów VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Miejsca, w którym można rozważyć, rozszerzanie modelu automatyzacji środowiska:  
  
-   Projekt  
  
-   dokument  
  
-   Kod  
  
-   Kompilacja  

  
Aby uzyskać więcej informacji na temat automatyzacji, zobacz [automatyzacji i rozszerzalności programu Visual Studio](../extensibility-in-visual-studio.md). Ten dokument i dokumentów zawiera łącza, aby łatwiej podejmować decyzje dotyczące sposobu powinien zapewnianie automatyzacji dla Twojego pakietu VSPackage.  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Tworzenie dodatku](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)