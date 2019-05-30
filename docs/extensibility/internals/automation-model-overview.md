---
title: Omówienie modelu automatyzacji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42b1237825eaa3fe2dec9ffa0142b78bc4693976
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326317"
---
# <a name="automation-model-overview"></a>Omówienie modelu automatyzacji
Model automatyzacji zawiera zestaw obiektów, wobec których można napisać dodatek programu Visual Studio lub rozszerzenia. Dodatek jest aplikacja, która może manipulować środowiska Visual Studio i automatyzacji typowych zadań. Rozszerzenia programu Visual Studio można tworzyć niestandardowe składniki programu Visual Studio lub dodać do funkcji składniki standardowe, takich jak edytor tekstu.

## <a name="objects-in-the-automation-model"></a>Obiekty w modelu automatyzacji
 Model automatyzacji składa się z powiązanych grup obiektów, które kontrolują główne aspekty wspólnego środowiska. Na poniższym diagramie przedstawiono obszerny zestaw obiektów programu Visual Studio, które tworzą model automatyzacji.

 ![Visual Studio automation object chart](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Aby uzyskać więcej informacji, zobacz [rozszerzanie środowiska Visual Studio](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).

 Środowisko udostępnia model dla różnych obszarów funkcjonalnych. Na przykład jest model kodu dla różnych elementów, które mogą być w kodzie. Brak model dokumentu do różnych elementów dokumentu. Jeden obszar, obszar projektu jest szczególne znaczenie w odniesieniu do dostawców pakietu VSPackage. Prawdopodobnie będziesz nowych typów projektów, aby współtworzyć modelu automatyzacji w podobny sposób jak [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Współtworzenie modelu automatyzacji. Czy proces jest opisany w [zapewnianie automatyzacji pakietów VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).

 Miejsca, w którym można rozważyć, rozszerzanie modelu automatyzacji środowiska:

- Projekt

- dokument

- Kod

- Kompilacja

Aby uzyskać więcej informacji na temat automatyzacji, zobacz [automatyzacji i rozszerzalności programu Visual Studio](../extensibility-in-visual-studio.md). Ten dokument i dokumentów zawiera łącza, aby łatwiej podejmować decyzje dotyczące sposobu powinien zapewnianie automatyzacji dla Twojego pakietu VSPackage.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie dodatku](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)