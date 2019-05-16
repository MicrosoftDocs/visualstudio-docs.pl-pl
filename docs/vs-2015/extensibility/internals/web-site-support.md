---
title: Obsługa witryny sieci Web | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1a96504783de466551c6fb9d055b95ba38df760
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687696"
---
# <a name="web-site-support"></a>Pomoc techniczna dotycząca witryny internetowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

System projektu witryny sieci Web jest system projektu, który tworzy projektów sieci Web. Projekty sieci Web z kolei tworzyć aplikacje sieci Web. Projekt witryny sieci Web wygenerowanie jednego pliku wykonywalnego, dla każdej strony sieci Web, który jest skojarzony kod. Dodatkowe pliki wykonywalne są generowane na podstawie plików kodu źródłowego w folderze /App_Code.  
  
 Systemy projektu witryny sieci Web są tworzone przez dodanie szablony i atrybuty rejestracji w istniejącym systemie projektu. Wybiera jeden z tych atrybutów dostawcy funkcji IntelliSense dla języka. Implementacja dostawcy IntelliSense obsługuje odwołania i wywołuje kompilator języka zleconą inteligentne strony sieci Web, która nie jest buforowana.  
  
 Kompilator języka używany do kompilowania stron sieci Web muszą być zarejestrowane w usłudze [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]. Możesz użyć [ \<kompilatora > Element](https://msdn.microsoft.com/library/7a151659-b803-4c27-b5ce-1c4aa0d5a823) w pliku Web.config, aby zarejestrować kompilatora, jak w poniższym przykładzie:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Szablony pomocy technicznej dotyczącej witryn internetowych](../../extensibility/internals/web-site-support-templates.md)  
 Wyświetla listę szablonów, które służy do tworzenia nowych projektów witryny sieci Web i skojarzone elementy.  
  
 [Atrybuty pomocy technicznej dotyczącej witryn internetowych](../../extensibility/internals/web-site-support-attributes.md)  
 Przedstawia informacje o atrybuty rejestracji, które łączą się z projektu witryny sieci Web, aby [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)].  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Projekty internetowe](../../extensibility/internals/web-projects.md)  
 Przedstawia omówienie dwa rodzaje projektów sieci Web, witryny sieci Web, projektów i projektów aplikacji sieci Web.
