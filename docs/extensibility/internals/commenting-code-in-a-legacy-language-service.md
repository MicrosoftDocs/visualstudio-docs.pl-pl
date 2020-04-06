---
title: Komentowanie kodu w starszej usłudze językowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5450199fde29f581dafdf9b2884c88ef26ea4ce7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709439"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Kod komentarza w starszej usłudze językowej
Języki programowania zazwyczaj zapewniają środki do dodawania adnotacji lub komentowania kodu. Komentarz to część tekstu, która zawiera dodatkowe informacje o kodzie, ale jest ignorowana podczas kompilacji lub interpretacji.

 Klasy frameworka zarządzanego pakietu (MPF) zapewniają obsługę komentowania i odkomentowywania zaznaczonego tekstu.

## <a name="comment-styles"></a>Style komentarzy
Istnieją dwa ogólne style komentarzy:

1. Komentarze wierszy, gdzie komentarz znajduje się w jednym wierszu.

2. Blokuj komentarze, w których komentarz może zawierać wiele wierszy.

Komentarze wierszy zazwyczaj mają znak początkowy (lub znaki), podczas gdy komentarze blokowe mają zarówno znaki początkowe, jak i końcowe. Na przykład w języku C#komentarz wiersza zaczyna się od `//` `/*` , a `*/`komentarz blokowy zaczyna się od .

Gdy użytkownik wybierze polecenie **Wybór komentarza** z menu **Edytuj** > **zaawansowane,** <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> polecenie jest <xref:Microsoft.VisualStudio.Package.Source> kierowane do metody w klasie. Gdy użytkownik wybierze polecenie **Uncomment Selection**, polecenie <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> jest kierowane do metody.

## <a name="support-code-comments"></a>Komentarze do kodu pomocy technicznej
 Możesz mieć swoje komentarze kod wsparcia usługi `EnableCommenting` języka za <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> pomocą nazwanego parametru . Spowoduje to <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> ustawienie <xref:Microsoft.VisualStudio.Package.LanguagePreferences> właściwości klasy. Aby uzyskać więcej informacji na temat ustawiania funkcji usługi języka, zobacz [Rejestrowanie starszej usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md).

 Należy również zastąpić <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> metodę, aby <xref:Microsoft.VisualStudio.Package.CommentInfo> zwrócić strukturę ze znakami komentarza dla języka. Domyślne są znaki komentarza wiersza w stylu C#.

### <a name="example"></a>Przykład
 Oto przykład implementacji <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> metody.

```csharp
using Microsoft.VisualStudio.Package;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override CommentInfo GetCommentFormat() {
            CommentInfo info = new CommentInfo();
            info.LineStart       = "//";
            info.BlockStart      = "/*";
            info.BlockEnd        = "*/";
            info.UseLineComments = true;
            return info;
        }
    }
}
```

## <a name="see-also"></a>Zobacz też
- [Starsze funkcje usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)
- [Rejestrowanie starszej usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)
