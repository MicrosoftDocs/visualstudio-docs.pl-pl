---
title: Omówienie modelu automatyzacji | Microsoft Docs
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
ms.openlocfilehash: 6ea38dc79bd557f17bbae8276dd112304c9a40fa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186739"
---
# <a name="automation-model-overview"></a>Omówienie modelu automatyzacji
Model automatyzacji składa się z zestawu obiektów, do którego można napisać dodatek lub rozszerzenie programu Visual Studio. Dodatek to aplikacja, która może manipulować środowiskiem programu Visual Studio i zautomatyzować typowe zadania. Rozszerzenie programu Visual Studio może tworzyć niestandardowe składniki programu Visual Studio lub dodawać do funkcji standardowych składników, takich jak edytor tekstu.

## <a name="objects-in-the-automation-model"></a>Obiekty w modelu automatyzacji
 Model automatyzacji składa się z pokrewnych grup obiektów kontrolujących główne aspekty wspólnego środowiska. Na poniższym diagramie przedstawiono rozbudowany zestaw obiektów programu Visual Studio, które tworzą model automatyzacji.

 ![Wykres obiektów automatyzacji programu Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Aby uzyskać więcej informacji, zobacz temat [zwiększanie środowiska programu Visual Studio](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).

 Środowisko zapewnia model dla różnych obszarów funkcjonalnych. Na przykład istnieje model kodu dla różnych elementów, które mogą znajdować się w kodzie. Istnieje model dokumentu dla różnych elementów dokumentu. Jeden obszar, obszar projektu, jest szczególnie interesujący dla dostawców pakietu VSPackage. Prawdopodobnie chcesz, aby nowe typy projektów współczyniły się do modelu automatyzacji w taki sam sposób jak [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] współtworzenia modelu automatyzacji. Ten proces jest opisany w temacie [zapewnianie automatyzacji dla pakietów VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).

 Miejsce, w którym można rozważyć rozszerzenie modelu automatyzacji środowiska:

- Projekt

- dokument

- Kod

- Kompilacja

Aby uzyskać więcej informacji na temat automatyzacji, zobacz [Automatyzacja i rozszerzalność dla programu Visual Studio](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015). Ten dokument i dokumenty, do których zawiera linki, ułatwiają podejmowanie decyzji dotyczących sposobu, w jaki należy zapewnić automatyzację pakietu VSPackage.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie dodatku](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)