---
title: Omówienie modelu automatyzacji | Microsoft Docs
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
ms.openlocfilehash: 83df8926be9cd7217c514a2ed3f242bf8e121913
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584571"
---
# <a name="automation-model-overview"></a>Omówienie modelu automatyzacji
Model automatyzacji składa się z zestawu obiektów, do którego można napisać dodatek lub rozszerzenie programu Visual Studio. Dodatek to aplikacja, która może manipulować środowiskiem programu Visual Studio i zautomatyzować typowe zadania. Rozszerzenie programu Visual Studio może tworzyć niestandardowe składniki programu Visual Studio lub dodawać do funkcji standardowych składników, takich jak edytor tekstu.

## <a name="objects-in-the-automation-model"></a>Obiekty w modelu automatyzacji
 Model automatyzacji składa się z pokrewnych grup obiektów kontrolujących główne aspekty wspólnego środowiska. Na poniższym diagramie przedstawiono rozbudowany zestaw obiektów programu Visual Studio, które tworzą model automatyzacji.

 ![Wykres obiektów automatyzacji programu Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Aby uzyskać więcej informacji, zobacz temat [zwiększanie środowiska programu Visual Studio](/previous-versions/esk3eey8(v=vs.140)).

 Środowisko zapewnia model dla różnych obszarów funkcjonalnych. Na przykład istnieje model kodu dla różnych elementów, które mogą znajdować się w kodzie. Istnieje model dokumentu dla różnych elementów dokumentu. Jeden obszar, obszar projektu, jest szczególnie interesujący dla dostawców pakietu VSPackage. Prawdopodobnie chcesz, aby nowe typy projektów współczyniły się do modelu automatyzacji w taki sam sposób jak [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] współtworzyć model automatyzacji. Ten proces jest opisany w temacie [zapewnianie automatyzacji dla pakietów VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).

 Miejsce, w którym można rozważyć rozszerzenie modelu automatyzacji środowiska:

- Project

- Dokument

- Kod

- Kompilacja

Aby uzyskać więcej informacji na temat automatyzacji, zobacz [Automatyzacja i rozszerzalność dla programu Visual Studio](../../vs-2015/extensibility/extensibility-in-visual-studio.md?view=vs-2015&preserve-view=true). Ten dokument i dokumenty, do których zawiera linki, ułatwiają podejmowanie decyzji dotyczących sposobu, w jaki należy zapewnić automatyzację pakietu VSPackage.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Tworzenie dodatku](/previous-versions/80493a3w(v=vs.140))