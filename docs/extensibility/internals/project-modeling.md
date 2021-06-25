---
title: Modelowanie projektu | Microsoft Docs
description: Dowiedz się więcej o standardowych obiektach projektu, które są wymagane do utworzenia automatyzacji dla nowego typu projektu, oraz o ścieżce, którą podąża automatyzacja projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b90271fcc43c627f2eb7dbb2f318427ad0d9839e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899683"
---
# <a name="project-modeling"></a>Modelowanie projektu
Następnym krokiem automatyzacji projektu jest zaimplementowanie standardowych obiektów projektu: kolekcji i , obiektów i oraz pozostałych obiektów unikatowych <xref:EnvDTE.Projects> `ProjectItems` dla `Project` <xref:EnvDTE.ProjectItem> implementacji. Te obiekty standardowe są zdefiniowane w pliku Dteinternal.h. Implementacja standardowych obiektów znajduje się w przykładzie BscPrj. Możesz użyć tych klas jako modeli do tworzenia własnych standardowych obiektów projektu, które są obok siebie obiektami projektu z innych typów projektów.

 Konsument automatyzacji zakłada, że może wywołać wywołania (" i ( ), gdzie n jest numerem indeksu w celu uzyskania <xref:EnvDTE.Solution> `<UniqueProjName>")` określonego projektu w <xref:EnvDTE.ProjectItems> `n` rozwiązaniu. Wykonanie tego wywołania automatyzacji powoduje, że środowisko wywołuje w odpowiedniej hierarchii projektu, przekazując VSITEMID_ROOT jako parametr ItemID i VSHPROPID_ExtObject jako parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> VSHPROPID. `IVsHierarchy::GetProperty` Zwraca wskaźnik `IDispatch` do obiektu automatyzacji zapewniającego interfejs `Project` podstawowy, który został zaimplementowany.

 Poniżej przedstawiono `IVsHierarchy::GetProperty` składnię .

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Projekty zmieszczą zagnieżdżanie i używają kolekcji do tworzenia grup elementów projektu. Hierarchia wygląda następująco.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Zagnieżdżanie <xref:EnvDTE.ProjectItem> oznacza, że obiekt może być <xref:EnvDTE.ProjectItems> kolekcją w tym samym czasie, ponieważ `ProjectItems` kolekcja może zawierać zagnieżdżone obiekty. W przykładzie Projektu podstawowego nie pokazano tego zagnieżdżania. Implementując obiekt , uczestniczysz w strukturze przypominanej drzewem, która charakteryzuje projekt `Project` ogólnego modelu automatyzacji.

 Automatyzacja projektu jest zgodna ze ścieżką na poniższym diagramie.

 ![Visual Studio obiektów projektu](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Automatyzacja projektu

 Jeśli obiekt nie zostanie zaimplementowany, środowisko nadal będzie zwracać obiekt ogólny `Project` `Project` zawierający tylko nazwę projektu.

## <a name="see-also"></a>Zobacz też
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
