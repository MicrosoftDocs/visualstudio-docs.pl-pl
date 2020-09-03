---
title: Kontrolka symbolu (pakietu VSPackage kontroli źródła) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9db1b4542eae293e39cda674fac3eb984aa77d3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708321"
---
# <a name="glyph-control-source-control-vspackage"></a>Kontrolka symbolu (pakietu VSPackage kontroli źródła)
Częścią głębokiej integracji dostępną do kontroli źródła pakietów VSPackage jest możliwość wyświetlania własnych symboli, aby wskazać stan elementów pod kontrolą źródła.

## <a name="levels-of-glyph-control"></a>Poziomy kontrolki glifów
 Symbol stanu jest ikoną wskazującą bieżący stan elementu, gdy jest wyświetlany, na przykład w **Eksplorator rozwiązań** lub **Widok klasy**. Pakietu VSPackage kontroli źródła może korzystać z dwóch poziomów kontrolki glifów. Może ograniczyć wybór glifów do wstępnie zdefiniowanego zestawu symboli dostarczonych przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE lub zdefiniować niestandardowy zestaw glifów do wyświetlenia.

### <a name="default-set-of-glyphs"></a>Domyślny zestaw glifów
 Aby określić glify stanu, które są skojarzone z elementem w **Eksplorator rozwiązań**, projekt żąda symbolu stanu z kontroli źródła przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> . Pakietu VSPackage kontroli źródła może zdecydować się na zachowanie wyboru glifów ograniczonych do wstępnie zdefiniowanych symboli dostarczonych przez IDE. W takim przypadku pakietu VSPackage przekazuje tablicę wartości reprezentujących wyliczenia symboli, które są zdefiniowane w *vsshell. idl*. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Jest to wstępnie zdefiniowany zestaw symboli ustawiany przez IDE, taki jak kłódki dla glifów zaewidencjonowanych i znacznik wyboru dla glifu zaznaczonego.

### <a name="custom-set-of-glyphs"></a>Niestandardowy zestaw symboli
 Pakietu VSPackage kontroli źródła może użyć własnych symboli do unikatowego wyglądu i działania podczas instalacji. Gdy nowy pakietu VSPackage kontroli źródła jest aktywny, powinien być w stanie rozpocząć korzystanie z własnych symboli, nawet jeśli poprzedni pakietu VSPackage kontroli źródła jest nadal załadowany, ale nieaktywny. W tym trybie pakietu VSPackage kontroli źródła nadal może korzystać z istniejących ikon, aby zachować spójność w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przypadku wybrania wyglądu.

 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>Usługa obsługuje interfejs, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> , który pakietu VSPackage może opcjonalnie zaimplementować i który zostanie poproszony przez IDE. Gdy IDE wykonuje żądanie, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] program podejmie próbę pobrania tego interfejsu z aktualnie zarejestrowanej kontroli źródła pakietu VSPackage. Jeśli interfejs istnieje w zarejestrowanych pakietu VSPackage, żądanie IDE dla symboli niestandardowych powiedzie się; w przeciwnym razie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE używa swojego domyślnego zestawu glifów.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A>Metoda jest używana przez program [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w celu uzyskania listy obrazów pokazujących różne stany kontroli źródła. Pakietu VSPackage kontroli źródła powraca do środowiska IDE uchwytu do listy obrazów dla jego niestandardowych symboli. IDE tworzy kopię listy obrazów w tym momencie i używa jej później do wybierania glifów do wyświetlenia. Jeśli nowy interfejs nie jest obsługiwany lub `IVsSccGlyphs::GetCustomGlyphList` Metoda zwraca `E_NOTIMPL` , wówczas IDE pobiera własne symbole z domyślnej listy symboli dostarczonych przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
