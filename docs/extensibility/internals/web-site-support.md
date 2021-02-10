---
title: Obsługa witryny sieci Web | Microsoft Docs
description: Informacje o systemach projektów witryn sieci Web, które są tworzone przez dodanie szablonów i atrybutów rejestracji do istniejącego systemu projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 141e4acf7db61130de859f38891670e69d3bd640
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940025"
---
# <a name="web-site-support"></a>Pomoc techniczna dotycząca witryny internetowej
System projektu witryny sieci Web to system projektu, który tworzy projekty sieci Web. Projekty sieci Web z kolei tworzą aplikacje sieci Web. Projekt witryny sieci Web generuje jeden plik wykonywalny dla każdej strony sieci Web, która ma skojarzony kod. Dodatkowe pliki wykonywalne są generowane na podstawie plików kodu źródłowego w folderze/App_Code.

 Systemy projektów witryny sieci Web są tworzone przez dodanie szablonów i atrybutów rejestracji do istniejącego systemu projektu. Jeden z tych atrybutów wybiera dostawcę IntelliSense dla danego języka. Implementacja dostawcy IntelliSense obsługuje odwołania i wywołuje kompilator języka, gdy zażądano inteligentnej strony sieci Web, która nie jest buforowana.

 Kompilator języka używany do kompilowania stron sieci Web musi być zarejestrowany w usłudze [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] . Aby zarejestrować kompilator, można użyć [ \<compiler> elementu](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) w pliku Web.config, jak w poniższym przykładzie:

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>W tej sekcji
- [Szablony pomocy technicznej dotyczącej witryn internetowych](../../extensibility/internals/web-site-support-templates.md)

 Wyświetla listę szablonów, których można użyć do tworzenia nowych projektów witryny sieci Web i skojarzonych z nimi elementów.

- [Atrybuty pomocy technicznej dotyczącej witryn internetowych](../../extensibility/internals/web-site-support-attributes.md)

 Przedstawia atrybuty rejestracji, które łączą projekt witryny sieci Web z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] .

## <a name="related-sections"></a>Sekcje pokrewne
- [Projekty internetowe](../../extensibility/internals/web-projects.md)

 Przedstawia przegląd dwóch rodzajów projektów sieci Web, projektów witryny sieci Web i projektów aplikacji sieci Web.
