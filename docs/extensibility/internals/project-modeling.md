---
title: Modelowanie projektów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1ac89baf5bc7582d3430532938a5e5a0c35a4c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706551"
---
# <a name="project-modeling"></a>Modelowanie projektu
Następnym krokiem w dostarczaniu automatyzacji dla projektu jest <xref:EnvDTE.Projects> `ProjectItems` zaimplementowanie standardowych obiektów projektu: i kolekcje; `Project` i <xref:EnvDTE.ProjectItem> przedmioty; i pozostałe obiekty unikatowe dla implementacji. Te standardowe obiekty są zdefiniowane w pliku Dteinternal.h. Implementacja standardowych obiektów znajduje się w próbce BscPrj. Te klasy można użyć jako modele do tworzenia własnych standardowych obiektów projektu, które stoją obok siebie z obiektów projektu z innych typów projektów.

 Konsument automatyzacji zakłada, że <xref:EnvDTE.Solution>będzie`<UniqueProjName>")` mógł <xref:EnvDTE.ProjectItems> `n`zadzwonić (" i ( ), gdzie n jest numerem indeksu w celu uzyskania określonego projektu w rozwiązaniu. Wykonanie tego wywołania automatyzacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> powoduje, że środowisko do wywołania odpowiedniej hierarchii projektu, przekazywanie VSITEMID_ROOT jako ItemID parametr i VSHPROPID_ExtObject jako parametr VSHPROPID. `IVsHierarchy::GetProperty`zwraca `IDispatch` wskaźnik do obiektu automatyzacji, zapewniając interfejs podstawowy, `Project` który został zaimplementowany.

 Poniżej znajduje się składnia . `IVsHierarchy::GetProperty`

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Projekty uwzględniają zagnieżdżanie i używają kolekcji do tworzenia grup elementów projektu. Hierarchia wygląda tak.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Zagnieżdżanie oznacza, że <xref:EnvDTE.ProjectItem> obiekt może być <xref:EnvDTE.ProjectItems> kolekcji w tym samym czasie, `ProjectItems` ponieważ kolekcja może zawierać zagnieżdżone obiekty. Przykład projektu podstawowego nie wykazuje tego zagnieżdżenia. Implementując `Project` obiekt, można uczestniczyć w strukturze drzewa, które charakteryzuje projekt ogólnego modelu automatyzacji.

 Automatyzacja projektu podąża ścieżką na poniższym diagramie.

 ![Obiekty programu Visual Studio Project](../../extensibility/internals/media/projectobjects.gif "ProjectObjects (ProjektObjects)") Automatyzacja projektów

 Jeśli obiekt nie `Project` zostanie zaimplementowany, `Project` środowisko nadal będzie zwracać ogólny obiekt, który zawiera tylko nazwę projektu.

## <a name="see-also"></a>Zobacz też
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
