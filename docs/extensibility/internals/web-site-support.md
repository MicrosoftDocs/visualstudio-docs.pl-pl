---
title: Pomoc techniczna witryny sieci Web | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22047ad1b0709cefa200656e61f8e0d39ace94c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703447"
---
# <a name="web-site-support"></a>Pomoc techniczna dotycząca witryny internetowej
System projektu witryny sieci Web to system projektu, który tworzy projekty sieci Web. Projekty sieci Web z kolei tworzą aplikacje sieci Web. Projekt witryny sieci Web generuje jeden plik wykonywalny dla każdej strony sieci Web, która ma skojarzony kod. Dodatkowe pliki wykonywalne są generowane z plików kodu źródłowego w /App_Code folderze.

 Systemy projektów witryny sieci Web są tworzone przez dodanie szablonów i atrybutów rejestracji do istniejącego systemu projektu. Jeden z tych atrybutów wybiera dostawcę intellisense dla języka. Implementacja dostawcy IntelliSense obsługuje odwołania i wywołuje kompilator języka, gdy żądana jest inteligentna strona sieci Web, która nie jest buforowana.

 Kompilator języka używany do kompilowania [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]stron sieci Web musi być zarejestrowany w pliku . [ \<Kompilatora> element](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) w pliku Web.config można użyć do zarejestrowania kompilatora, tak jak w poniższym przykładzie:

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>W tej sekcji
- [Szablony pomocy technicznej dotyczącej witryn internetowych](../../extensibility/internals/web-site-support-templates.md)

 Wyświetla listę szablonów, za pomocą których można tworzyć nowe projekty witryn sieci Web i skojarzone elementy.

- [Atrybuty pomocy technicznej dotyczącej witryn internetowych](../../extensibility/internals/web-site-support-attributes.md)

 Przedstawia atrybuty rejestracji łączące projekt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] witryny sieci Web z i [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)].

## <a name="related-sections"></a>Sekcje pokrewne
- [Projekty internetowe](../../extensibility/internals/web-projects.md)

 Przedstawia omówienie dwóch rodzajów projektów sieci Web, projektów witryn sieci Web i projektów aplikacji sieci Web.
