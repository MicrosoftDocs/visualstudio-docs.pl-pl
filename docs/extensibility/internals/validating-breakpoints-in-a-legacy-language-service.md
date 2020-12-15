---
title: Sprawdzanie poprawności punktów przerwania w starszej wersji usługi językowej | Microsoft Docs
description: Dowiedz się, jak zastąpić metodę ValidateBreakpointLocation w starszej wersji usługi językowej, aby sprawdzić poprawność punktów przerwania przed uruchomieniem debugera.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d48db7397e2f9a5921315036bea15551fb7baa9
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488027"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Sprawdzanie poprawności punktów przerwania w starszej wersji usługi językowej
Punkt przerwania wskazuje, że wykonanie programu powinno zostać zatrzymane w określonym momencie, gdy jest uruchamiane w debugerze. Użytkownik może umieścić punkt przerwania w dowolnym wierszu w pliku źródłowym, ponieważ Edytor nie ma informacji o tym, co stanowi prawidłową lokalizację punktu przerwania. Po uruchomieniu debugera wszystkie oznaczone punkty przerwania (nazywane punktami przerwania w toku) są powiązane z odpowiednią lokalizacją w uruchomionym programie. W tym samym czasie punkty przerwania są sprawdzane, aby upewnić się, że oznaczają poprawne lokalizacje kodu. Na przykład punkt przerwania komentarza jest nieprawidłowy, ponieważ nie ma kodu w tej lokalizacji w kodzie źródłowym. Debuger wyłącza nieprawidłowe punkty przerwania.

 Ponieważ usługa językowa wie o wyświetlanym kodzie źródłowym, może sprawdzić poprawność punktów przerwania przed uruchomieniem debugera. Można zastąpić <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metodę w celu zwrócenia zakresu określającego prawidłową lokalizację dla punktu przerwania. Lokalizacja punktu przerwania jest nadal weryfikowana, gdy zostanie uruchomiony debuger, ale użytkownik jest powiadamiany o nieprawidłowych punktach przerwania bez oczekiwania na załadowanie debugera.

## <a name="implementing-support-for-validating-breakpoints"></a>Implementowanie obsługi walidacji punktów przerwania

- <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>Metoda otrzymuje pozycję punktu przerwania. Twoja implementacja musi zdecydować, czy lokalizacja jest prawidłowa, i wskazać ją poprzez zwrócenie zakresu tekstu, który identyfikuje kod skojarzony z wierszem Umieść punkt przerwania.

- Zwróć <xref:Microsoft.VisualStudio.VSConstants.S_OK> , jeśli lokalizacja jest prawidłowa, lub <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> Jeśli nie jest prawidłowa.

- Jeśli punkt przerwania jest prawidłowy, zakres tekstu jest wyróżniony wraz z punktem przerwania.

- Jeśli punkt przerwania jest nieprawidłowy, na pasku stanu pojawi się komunikat o błędzie.

### <a name="example"></a>Przykład
 W tym przykładzie przedstawiono implementację <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metody, która wywołuje parser w celu uzyskania zakresu kodu (jeśli istnieje) w określonej lokalizacji.

 W tym przykładzie przyjęto założenie, że dodano `GetCodeSpan` metodę do <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasy, która sprawdza poprawność zakresu tekstu i zwraca, `true` Jeśli jest prawidłową lokalizacją punktu przerwania.

```csharp
using Microsoft VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,
                                                       int line,
                                                       int col,
                                                       TextSpan[] pCodeSpan)
        {
            int retval = VSConstants.S_FALSE;
            if (pCodeSpan != null)
            {
                // Initialize span to current line by default.
                pCodeSpan[0].iStartLine = line;
                pCodeSpan[0].iStartIndex = col;
                pCodeSpan[0].iEndLine = line;
                pCodeSpan[0].iEndIndex = col;
            }

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
                                                              ParseReason.CodeSpan,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        TextSpan span = new TextSpan();
                        if (sink.GetCodeSpan(out span))
                        {
                            pCodeSpan[0] = span;
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

## <a name="see-also"></a>Zobacz także
- [Funkcje starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)
