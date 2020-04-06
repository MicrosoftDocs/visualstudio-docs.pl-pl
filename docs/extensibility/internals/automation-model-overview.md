---
title: Omówienie modelu automatyzacji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b940677c370106ebdcc63c7984d553003251e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710010"
---
# <a name="automation-model-overview"></a>Omówienie modelu automatyzacji
Model automatyzacji składa się z zestawu obiektów, na których można napisać dodatek lub rozszerzenie programu Visual Studio. Dodatek to aplikacja, która może manipulować środowiskiem Visual Studio i zautomatyzować typowe zadania. Rozszerzenie programu Visual Studio można utworzyć niestandardowe składniki programu Visual Studio lub dodać do funkcji standardowych składników, takich jak edytor tekstu.

## <a name="objects-in-the-automation-model"></a>Obiekty w modelu automatyzacji
 Model automatyzacji składa się z powiązanych grup obiektów, które kontrolują główne aspekty wspólnego środowiska. Na poniższym diagramie przedstawiono obszerny zestaw obiektów programu Visual Studio, które tworzą model automatyzacji.

 ![Wykres obiektów automatyzacji programu Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Aby uzyskać więcej informacji, zobacz [Rozszerzanie środowiska programu Visual Studio](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).

 Środowisko zapewnia model dla różnych obszarów funkcjonalnych. Na przykład istnieje model kodu dla różnych elementów, które można znaleźć w kodzie. Istnieje model dokumentu dla różnych elementów dokumentu. Jeden obszar, obszar projektu, jest szczególnie interesujące dla dostawców VSPackage. Prawdopodobnie chcesz, aby nowe typy projektów przyczyniać się do [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] modelu automatyzacji w taki sam sposób, jak i przyczynić się do modelu automatyzacji. Ten proces jest opisany w [provide automatyzacji vsPackages](../../extensibility/internals/providing-automation-for-vspackages.md).

 Miejsca, w których można rozważyć rozszerzenie modelu automatyzacji środowiska:

- Projekt

- Dokument

- Code

- Kompilacja

Aby uzyskać więcej informacji na temat automatyzacji, zobacz [Automatyzacja i rozszerzalność programu Visual Studio](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015). Ten dokument i dokumenty, które zawiera łącza do, pomoc w podejmowaniu decyzji dotyczących sposobu zapewnienia automatyzacji dla vsPackage.

## <a name="see-also"></a>Zobacz też
- [Jak: Tworzenie dodatku](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
