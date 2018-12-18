---
title: Omówienie modelu automatyzacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd1e8ced29b1b1b090fd0feabca93f23dcb67a15
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809678"
---
# <a name="automation-model-overview"></a>Omówienie modelu automatyzacji
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Model automatyzacji zawiera zestaw obiektów, wobec których można napisać dodatek programu Visual Studio lub rozszerzenia. Dodatek jest aplikacja, która może manipulować środowiska Visual Studio i automatyzacji typowych zadań. Rozszerzenia programu Visual Studio można tworzyć niestandardowe składniki programu Visual Studio lub dodać do funkcji składniki standardowe, takich jak edytor tekstu.  
  
## <a name="objects-in-the-automation-model"></a>Obiekty w modelu automatyzacji  
 Model automatyzacji składa się z powiązanych grup obiektów, które kontrolują główne aspekty wspólnego środowiska. Oto diagram, który zawiera obszerny zestaw obiektów, które tworzą model automatyzacji.  
  
 ![Wykres obiektu automatyzacji w usłudze Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Obiekty automatyzacji w usłudze Visual Studio  
  
 Aby uzyskać więcej informacji, zobacz [rozszerzanie środowiska programu Visual Studio](http://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 Środowisko udostępnia model dla różnych obszarów funkcjonalnych. Na przykład jest model kodu dla różnych elementów, które mogą być w kodzie. Brak model dokumentu do różnych elementów dokumentu. Jeden obszar, obszar projektu jest szczególne znaczenie w odniesieniu do dostawców pakietu VSPackage. Prawdopodobnie będziesz nowych typów projektów, aby współtworzyć modelu automatyzacji w podobny sposób jak [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] i [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Współtworzenie modelu automatyzacji. Czy proces jest opisany w [zapewnianie automatyzacji pakietów VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Miejsca, w którym można rozważyć, rozszerzanie modelu automatyzacji środowiska:  
  
- Projekt  
  
- dokument  
  
- Kod  
  
- Kompilacja  
  
  Aby uzyskać więcej informacji na temat automatyzacji, zobacz [automatyzacji i rozszerzalności programu Visual Studio](http://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Ten dokument i dokumentów zawiera łącza, aby łatwiej podejmować decyzje dotyczące sposobu powinien zapewnianie automatyzacji dla Twojego pakietu VSPackage.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Tworzenie dodatku](http://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)

