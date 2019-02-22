---
title: Projekt modelowania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a2ae395d94d76fd2b11de33cc6d5053d8b92432
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633437"
---
# <a name="project-modeling"></a>Modelowanie projektu
Następnym krokiem w zapewnianie automatyzacji dla projektu jest zaimplementowanie obiektów standardowy projekt: <xref:EnvDTE.Projects> i `ProjectItems` kolekcji; `Project` i <xref:EnvDTE.ProjectItem> obiekty; i pozostałe obiekty unikatowy dla implementacji. Te standardowe obiekty są zdefiniowane w pliku Dteinternal.h. Implementacja standardowych obiektów znajduje się w próbce BscPrj. Można użyć tych klas jako modele do tworzenia własnych obiektów standardowy projekt, które utrudniają korzystanie z side-by-side przy użyciu obiektów projektu z innych typów projektów.

 Zakłada konsumenta automatyzacji, aby można było wywołać <xref:EnvDTE.Solution>("`<UniqueProjName>")` i <xref:EnvDTE.ProjectItems> (`n`) gdzie n to numer indeksu, umożliwiającą uzyskanie określonego projektu w rozwiązaniu. Wywołania usługi automation powoduje, że do środowiska, aby wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> na odpowiedni projekt hierarchii, przekazując VSITEMID_ROOT jako parametr ItemID i VSHPROPID_ExtObject jako parametr VSHPROPID. `IVsHierarchy::GetProperty` Zwraca `IDispatch` wskaźnik do obiektu automatyzacji, podając podstawowe `Project` interfejs, który został zaimplementowany.

 Poniżej przedstawiono składnię `IVsHierarchy::GetProperty`.

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT``*pvar`

 `);`

 Projekty uwzględnić zagnieżdżanie i tworzenia grup elementów projektu za pomocą kolekcji. Hierarchia wygląda następująco.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Zagnieżdżanie oznacza, że <xref:EnvDTE.ProjectItem> obiekt może być <xref:EnvDTE.ProjectItems> kolekcji, w tym samym czasie ponieważ `ProjectItems` Kolekcja może zawierać obiekty zagnieżdżone. Przykład podstawowego projektu nie przedstawiono tu to zagnieżdżania. Implementując `Project` obiektu uczestniczyć w strukturze drzewa, który charakteryzuje Projekt modelu automatyzacji ogólnej.

 Automatyzacja projektu postępuje zgodnie ze ścieżką na poniższym diagramie.

 ![Obiekty projektu usługi Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") projektu automatyzacji

 Jeśli nie należy implementować `Project` obiektu, środowiska nadal będzie zwracać ogólnego `Project` obiekt, który zawiera tylko nazwę projektu.

## <a name="see-also"></a>Zobacz też
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>