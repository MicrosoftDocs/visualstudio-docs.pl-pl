---
title: Omówienie modelu automatyzacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e17164976062ec916074c6210be6ae42e8ea1d03
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699510"
---
# <a name="automation-model-overview"></a>Omówienie modelu automatyzacji
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Model automatyzacji składa się z zestawu obiektów, do którego można napisać dodatek lub rozszerzenie programu Visual Studio. Dodatek to aplikacja, która może manipulować środowiskiem programu Visual Studio i zautomatyzować typowe zadania. Rozszerzenie programu Visual Studio może tworzyć niestandardowe składniki programu Visual Studio lub dodawać do funkcji standardowych składników, takich jak edytor tekstu.  
  
## <a name="objects-in-the-automation-model"></a>Obiekty w modelu automatyzacji  
 Model automatyzacji składa się z pokrewnych grup obiektów kontrolujących główne aspekty wspólnego środowiska. Poniżej znajduje się diagram pokazujący obszerny zestaw obiektów, które tworzą model automatyzacji.  
  
 ![Wykres obiektów automatyzacji programu Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Obiekty automatyzacji programu Visual Studio  
  
 Aby uzyskać więcej informacji, zobacz [rozszerzanie środowiska programu Visual Studio](https://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 Środowisko zapewnia model dla różnych obszarów funkcjonalnych. Na przykład istnieje model kodu dla różnych elementów, które mogą znajdować się w kodzie. Istnieje model dokumentu dla różnych elementów dokumentu. Jeden obszar, obszar projektu, jest szczególnie interesujący dla dostawców pakietu VSPackage. Prawdopodobnie chcesz, aby nowe typy projektów współczyniły się do modelu automatyzacji w taki sam sposób jak [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] i [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] współtworzyć model automatyzacji. Ten proces jest opisany w temacie [zapewnianie automatyzacji dla pakietów VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Miejsce, w którym można rozważyć rozszerzenie modelu automatyzacji środowiska:  
  
- Projekt  
  
- Dokument  
  
- Kod  
  
- Kompilacja  
  
  Aby uzyskać więcej informacji na temat automatyzacji, zobacz [Automatyzacja i rozszerzalność dla programu Visual Studio](https://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Ten dokument i dokumenty, do których zawiera linki, ułatwiają podejmowanie decyzji dotyczących sposobu, w jaki należy zapewnić automatyzację pakietu VSPackage.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Tworzenie dodatku](https://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
