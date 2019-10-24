---
title: Modelowanie projektu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42e810a36478e49a578c6713d20f1bfc6be98309
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725559"
---
# <a name="project-modeling"></a>Modelowanie projektu
Następnym krokiem w celu zapewnienia automatyzacji projektu jest zaimplementowanie standardowych obiektów projektu: kolekcji <xref:EnvDTE.Projects> i `ProjectItems`; obiekty `Project` i <xref:EnvDTE.ProjectItem>; i pozostałe obiekty, które są unikatowe dla Twojej implementacji. Te standardowe obiekty są zdefiniowane w pliku Dteinternal. h. Implementacja standardowych obiektów znajduje się w próbce BscPrj. Tych klas można używać jako modeli do tworzenia własnych standardowych obiektów projektu, które obok siebie są obiektami projektów z innych typów projektów.

 Odbiorca automatyzacji zakłada, że może wywoływać <xref:EnvDTE.Solution> ("`<UniqueProjName>")` i <xref:EnvDTE.ProjectItems> (`n`), gdzie n jest numerem indeksu do uzyskania określonego projektu w rozwiązaniu. Wykonanie tego wywołania automatyzacji powoduje, że środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> w odpowiedniej hierarchii projektu, przekazując VSITEMID_ROOT jako parametr ItemID i VSHPROPID_ExtObject jako parametr VSHPROPID. `IVsHierarchy::GetProperty` zwraca wskaźnik `IDispatch` do obiektu automatyzacji dostarczającego podstawowy interfejs `Project`, który został zaimplementowany.

 Poniżej przedstawiono składnię `IVsHierarchy::GetProperty`.

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT``*pvar`

 `);`

 Projekty umożliwiają zagnieżdżanie i Używanie kolekcji do tworzenia grup elementów projektu. Hierarchia wygląda następująco.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Zagnieżdżanie oznacza, że <xref:EnvDTE.ProjectItem> obiektu może być <xref:EnvDTE.ProjectItems> kolekcji w tym samym czasie, ponieważ kolekcja `ProjectItems` może zawierać obiekty zagnieżdżone. Przykład projektu podstawowego nie pokazuje tego zagnieżdżenia. Implementując obiekt `Project`, należy wziąć udział w strukturze podobnej do drzewa, która charakteryzuje projekt ogólnego modelu automatyzacji.

 Automatyzacja projektu następuje po ścieżce na poniższym diagramie.

 ![Obiekty projektu programu Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Automatyzacja projektu

 Jeśli obiekt `Project` nie zostanie wdrożony, środowisko będzie nadal zwracać ogólny obiekt `Project`, który zawiera tylko nazwę projektu.

## <a name="see-also"></a>Zobacz także
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>