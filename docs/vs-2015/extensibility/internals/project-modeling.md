---
title: Modelowanie projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e0edca4a45419a4a4c962ebf62b65e99c4732a12
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431385"
---
# <a name="project-modeling"></a>Modelowanie projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Następnym krokiem w celu zapewnienia automatyzacji projektu jest zaimplementowanie standardowych obiektów projektu: <xref:EnvDTE.Projects> kolekcja i, `ProjectItems` `Project` <xref:EnvDTE.ProjectItem> obiekty i oraz pozostałe obiekty, które są unikatowe dla implementacji. Te standardowe obiekty są zdefiniowane w pliku Dteinternal. h. Implementacja standardowych obiektów znajduje się w próbce BscPrj. Tych klas można używać jako modeli do tworzenia własnych standardowych obiektów projektu, które obok siebie są obiektami projektów z innych typów projektów.  
  
 Odbiorca automatyzacji ma możliwość wywołania <xref:EnvDTE.Solution> (" `<UniqueProjName>")` i <xref:EnvDTE.ProjectItems> ( `n` ), gdzie n jest numerem indeksu do uzyskania określonego projektu w rozwiązaniu. Wykonanie tego wywołania automatyzacji powoduje, że środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> odpowiednią hierarchię projektu, przekazując VSITEMID_ROOT jako parametr ItemId i VSHPROPID_ExtObject jako parametr VSHPROPID. `IVsHierarchy::GetProperty` zwraca `IDispatch` wskaźnik do obiektu automatyzacji dostarczającego `Project` interfejs podstawowy, który został zaimplementowany.  
  
 Poniżej przedstawiono składnię polecenia `IVsHierarchy::GetProperty` .  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Projekty umożliwiają zagnieżdżanie i Używanie kolekcji do tworzenia grup elementów projektu. Hierarchia wygląda następująco.  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 Zagnieżdżanie oznacza, że <xref:EnvDTE.ProjectItem> obiekt może być <xref:EnvDTE.ProjectItems> kolekcją w tym samym czasie, ponieważ `ProjectItems` Kolekcja może zawierać zagnieżdżonych obiektów. Przykład projektu podstawowego nie pokazuje tego zagnieżdżenia. Implementując `Project` obiekt, należy wziąć udział w strukturze podobnej do drzewa, która charakteryzuje projekt ogólnego modelu automatyzacji.  
  
 Automatyzacja projektu następuje po ścieżce na poniższym diagramie.  
  
 ![Obiekty projektu programu Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Automatyzacja projektu  
  
 Jeśli obiekt nie zostanie wdrożony `Project` , środowisko nadal zwróci obiekt generyczny `Project` , który zawiera tylko nazwę projektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>
