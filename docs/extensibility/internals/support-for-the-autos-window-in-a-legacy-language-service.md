---
title: Obsługa okna autoodtwarzania w starszej wersji usługi językowej
description: Dowiedz się, jak zaimplementować obsługę okna Autowypełniania, w którym są wyświetlane wyrażenia, które są w zakresie, gdy debugowany program jest wstrzymany.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 70a8697027cde07ca2b30d01a73a80d771155c5c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080635"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Obsługa okna autoodtwarzania w starszej wersji usługi językowej

W oknie **samochody** są wyświetlane wyrażenia, takie jak zmienne i parametry, które są w zakresie, gdy debugowany program jest wstrzymany (z powodu punktu przerwania lub wyjątku). Wyrażenia mogą zawierać zmienne, lokalne lub globalne oraz parametry, które zostały zmienione w zakresie lokalnym. Okno **autouzupełniania** może również zawierać wystąpienia klasy, struktury lub innego typu. Wszystkie elementy, które może oszacować ewaluatora wyrażeń, mogą być wyświetlane w oknie **Autokorekty** .

 Struktura pakietu zarządzanego (MPF) nie zapewnia bezpośredniej pomocy technicznej **dla okna.** Jednak w przypadku zastąpienia <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metody można zwrócić listę wyrażeń, które mają być prezentowane w oknie **Automatyczne** .

## <a name="implementing-support-for-the-autos-window"></a>Implementowanie obsługi okna Autokorekty

 Wszystko, co musisz zrobić, aby obsłużyć okno **autostarts** , zaimplementuj <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metodę w <xref:Microsoft.VisualStudio.Package.LanguageService> klasie. Twoja implementacja musi podejmować decyzje dotyczące lokalizacji w pliku źródłowym, które powinny być wyświetlane w oknie **Autokorekty** . Metoda zwraca listę ciągów, w których każdy ciąg reprezentuje pojedyncze wyrażenie. Zwracana wartość wskazuje, <xref:Microsoft.VisualStudio.VSConstants.S_OK> że lista zawiera wyrażenia, natomiast <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> wskazuje, że nie ma żadnych wyrażeń do wyświetlenia.

 Zwracane wyrażenia są nazwami zmiennych lub parametrów, które pojawiają się w tej lokalizacji w kodzie. Te nazwy są przenoszone do ewaluatora wyrażeń w celu uzyskania wartości i typów, które są następnie wyświetlane **w oknie zmiennych** .

### <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono implementację <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metody, która pobiera listę wyrażeń z <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody przy użyciu przyczyny analizy <xref:Microsoft.VisualStudio.Package.ParseReason> . Każde wyrażenie jest opakowane jako `TestVsEnumBSTR` implementujący <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> interfejs.

 Należy zauważyć, `GetAutoExpressionsCount` że `GetAutoExpression` metody i są metodami niestandardowymi dla `TestAuthoringSink` obiektu i zostały dodane do obsługi tego przykładu. Reprezentują one jeden ze sposobów, w których wyrażenia dodawane do `TestAuthoringSink` obiektu przez analizator (poprzez wywoływanie <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> metody) są dostępne poza analizatorem.

```csharp
using Microsoft.VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override int GetProximityExpressions(IVsTextBuffer buffer,
                                                    int line,
                                                    int col,
                                                    int cLines,
                                                    out IVsEnumBSTR ppEnum)
        {
            int retval = VSConstants.E_NOTIMPL;
            ppEnum = null;
            if (buffer != null)
            {
                IVsTextLines textLines = buffer as IVsTextLines;
                if (textLines != null)
                {
                    Source src = this.GetSource(textLines);
                    if (src != null)
                    {
                        TokenInfo tokenInfo = new TokenInfo();
                        string text = src.GetText();
                        ParseRequest req = CreateParseRequest(src,
                                                              line,
                                                              col,
                                                              tokenInfo,
                                                              text,
                                                              src.GetFilePath(),
                                                              ParseReason.Autos,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        retval = VSConstants.S_FALSE;
                        int spanCount = sink.GetAutoExpressionsCount();
                        if (spanCount > 0) {
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();
                            for (int i = 0; i < spanCount; i++)
                            {
                                TextSpan span;
                                sink.GetAutoExpression(i, out span);
                                string expression = src.GetText(span.iStartLine,
                                                                span.iStartIndex,
                                                                span.iEndLine,
                                                                span.iEndIndex);
                                bstrList.AddString(expression);
                            }
                            ppEnum = bstrList;
                            retval = VSConstants.S_OK;
                        }
                    }
                }
            }
            return retval;
        }
    }
}
```
