---
title: Obsługa witryny sieci Web | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687696"
---
# <a name="web-site-support"></a>Pomoc techniczna dotycząca witryny internetowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

System projektu witryny sieci Web to system projektu, który tworzy projekty sieci Web. Projekty sieci Web z kolei tworzą aplikacje sieci Web. Projekt witryny sieci Web generuje jeden plik wykonywalny dla każdej strony sieci Web, która ma skojarzony kod. Dodatkowe pliki wykonywalne są generowane na podstawie plików kodu źródłowego w folderze/App_Code.  
  
 Systemy projektów witryny sieci Web są tworzone przez dodanie szablonów i atrybutów rejestracji do istniejącego systemu projektu. Jeden z tych atrybutów wybiera dostawcę IntelliSense dla danego języka. Implementacja dostawcy IntelliSense obsługuje odwołania i wywołuje kompilator języka, gdy zażądano inteligentnej strony sieci Web, która nie jest buforowana.  
  
 Kompilator języka używany do kompilowania stron sieci Web musi być zarejestrowany w usłudze [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] . Aby zarejestrować kompilator, można użyć [ \<compiler> elementu](https://msdn.microsoft.com/library/7a151659-b803-4c27-b5ce-1c4aa0d5a823) w pliku Web.config, jak w poniższym przykładzie:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Szablony pomocy technicznej dotyczącej witryn internetowych](../../extensibility/internals/web-site-support-templates.md)  
 Wyświetla listę szablonów, których można użyć do tworzenia nowych projektów witryny sieci Web i skojarzonych z nimi elementów.  
  
 [Atrybuty pomocy technicznej dotyczącej witryn internetowych](../../extensibility/internals/web-site-support-attributes.md)  
 Przedstawia atrybuty rejestracji, które łączą projekt witryny sieci Web z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] .  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Projekty internetowe](../../extensibility/internals/web-projects.md)  
 Przedstawia przegląd dwóch rodzajów projektów sieci Web, projektów witryny sieci Web i projektów aplikacji sieci Web.
