---
title: Komentowanie kodu w starszej wersji usługi językowej | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709439"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Dodawanie komentarza do kodu w starszej wersji usługi językowej
Języki programowania zwykle umożliwiają dodawanie adnotacji do kodu lub komentowanie go. Komentarz to sekcja tekstu, która zawiera dodatkowe informacje o kodzie, ale jest ignorowany podczas kompilowania lub interpretacji.

 Klasy struktury pakietu zarządzanego (MPF) zapewniają obsługę komentowania i usuwania komentarzy zaznaczonego tekstu.

## <a name="comment-styles"></a>Style komentarzy
Istnieją dwa ogólne style komentarzy:

1. Komentarze liniowe, gdzie komentarz znajduje się w jednym wierszu.

2. Blokuj komentarze, gdzie komentarz może zawierać wiele wierszy.

Komentarze liniowe zwykle mają znak początkowy (lub znaki), natomiast Komentarze blokowe mają znaki początkowe i końcowe. Na przykład w języku C# komentarz do linii zaczyna się od `//` , a komentarz bloku zaczyna się od `/*` i zaczyna się od `*/` .

Gdy użytkownik wybierze **wybór komentarza** z polecenia z menu **Edytuj**  >  **Zaawansowane** , polecenie jest kierowane do <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> metody <xref:Microsoft.VisualStudio.Package.Source> klasy. Gdy użytkownik wybierze polecenie **Usuń komentarz z zaznaczenia**, polecenie jest kierowane do <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> metody.

## <a name="support-code-comments"></a>Obsługa komentarzy do kodu
 Usługa językowa może obsługiwać komentarze w kodzie za pomocą `EnableCommenting` parametru nazwanego <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Ustawia <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> Właściwość <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy. Aby uzyskać więcej informacji na temat ustawiania funkcji usługi językowej, zobacz [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md).

 Należy również zastąpić metodę, <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> Aby zwrócić <xref:Microsoft.VisualStudio.Package.CommentInfo> strukturę z znakami komentarza dla danego języka. Znaki komentarza w stylu języka C# są domyślne.

### <a name="example"></a>Przykład
 Poniżej przedstawiono przykładową implementację <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> metody.

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
- [Funkcje starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)
- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)
