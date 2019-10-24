---
title: Sprawdzanie poprawności punktów przerwania w starszej wersji usługi językowej | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e7c46473610c96779d0c54e06e82cf884216b13b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722012"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Sprawdzanie poprawności punktów przerwania w starszej wersji usługi językowej
Punkt przerwania wskazuje, że wykonanie programu powinno zostać zatrzymane w określonym momencie, gdy jest uruchamiane w debugerze. Użytkownik może umieścić punkt przerwania w dowolnym wierszu w pliku źródłowym, ponieważ Edytor nie ma informacji o tym, co stanowi prawidłową lokalizację punktu przerwania. Po uruchomieniu debugera wszystkie oznaczone punkty przerwania (nazywane punktami przerwania w toku) są powiązane z odpowiednią lokalizacją w uruchomionym programie. W tym samym czasie punkty przerwania są sprawdzane, aby upewnić się, że oznaczają poprawne lokalizacje kodu. Na przykład punkt przerwania komentarza jest nieprawidłowy, ponieważ nie ma kodu w tej lokalizacji w kodzie źródłowym. Debuger wyłącza nieprawidłowe punkty przerwania.

 Ponieważ usługa językowa wie o wyświetlanym kodzie źródłowym, może sprawdzić poprawność punktów przerwania przed uruchomieniem debugera. Można zastąpić metodę <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>, aby zwrócić zakres określający prawidłową lokalizację dla punktu przerwania. Lokalizacja punktu przerwania jest nadal weryfikowana, gdy zostanie uruchomiony debuger, ale użytkownik jest powiadamiany o nieprawidłowych punktach przerwania bez oczekiwania na załadowanie debugera.

## <a name="implementing-support-for-validating-breakpoints"></a>Implementowanie obsługi walidacji punktów przerwania

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> otrzymuje pozycję punktu przerwania. Twoja implementacja musi zdecydować, czy lokalizacja jest prawidłowa, i wskazać ją poprzez zwrócenie zakresu tekstu, który identyfikuje kod skojarzony z wierszem Umieść punkt przerwania.

- Zwróć <xref:Microsoft.VisualStudio.VSConstants.S_OK>, jeśli lokalizacja jest prawidłowa, lub <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>, jeśli jest nieprawidłowa.

- Jeśli punkt przerwania jest prawidłowy, zakres tekstu jest wyróżniony wraz z punktem przerwania.

- Jeśli punkt przerwania jest nieprawidłowy, na pasku stanu pojawi się komunikat o błędzie.

### <a name="example"></a>Przykład
 W tym przykładzie przedstawiono implementację metody <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>, która wywołuje parser w celu uzyskania zakresu kodu (jeśli istnieje) w określonej lokalizacji.

 W tym przykładzie przyjęto założenie, że dodano metodę `GetCodeSpan` do klasy <xref:Microsoft.VisualStudio.Package.AuthoringSink>, która sprawdza poprawność zakresu tekstu i zwraca `true`, jeśli jest prawidłową lokalizacją punktu przerwania.

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