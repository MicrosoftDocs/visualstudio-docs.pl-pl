---
title: Kontrola glifów (Kontrola źródła VSPackage) | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708321"
---
# <a name="glyph-control-source-control-vspackage"></a>Kontrola glifa (kontrola źródła VSPackage)
Część głębokiej integracji dostępne do kontroli źródła VSPackages jest możliwość wyświetlania własnych glifów, aby wskazać stan elementów pod kontrolą źródła.

## <a name="levels-of-glyph-control"></a>Poziomy kontroli glifów
 Glif stanu to ikona wskazująca bieżący stan elementu podczas wyświetlania, na przykład w **Eksploratorze rozwiązań** lub w **widoku klasy**. Formant źródła VSPackage może wykonywać dwa poziomy kontroli glifów. Może ograniczyć wybór glifów do wstępnie zdefiniowanego zestawu glifów [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostarczonych przez IDE lub może zdefiniować niestandardowy zestaw glifów, które mają być wyświetlane.

### <a name="default-set-of-glyphs"></a>Domyślny zestaw glifów
 Aby określić glify stanu, które są skojarzone z elementem w **Eksploratorze rozwiązań,** projekt żąda glifu stanu z kontroli źródła za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>pliku . Kontrola źródła VSPackage może zdecydować, aby zachować wybór glifów ograniczone do wstępnie zdefiniowanych glifów dostarczonych przez IDE. W takim przypadku VSPackage przekazuje z powrotem tablicę wartości reprezentujących wyliczenia glifów, które są zdefiniowane w *vsshell.idl*. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Jest to wstępnie zdefiniowany zestaw glifów ustawionych przez IDE, takich jak kłódka dla glifów zaewidencjonowanych i znacznik wyboru dla wyewidencjonowanego glifa.

### <a name="custom-set-of-glyphs"></a>Niestandardowy zestaw glifów
 Formant źródła VSPackage można użyć własnych glifów dla unikatowy wygląd i działanie, gdy jest zainstalowany. Gdy nowy formant źródła VSPackage jest aktywny, powinno być w stanie rozpocząć korzystanie z własnych glifów, nawet jeśli poprzedni formant źródła VSPackage jest nadal ładowany, ale nieaktywny. W tym trybie formantu źródła VSPackage nadal można użyć istniejących [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ikon w celu utrzymania wygląd spójne z jeśli zdecyduje.

 Usługa <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> obsługuje interfejs, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>który VSPackage opcjonalnie można zaimplementować i który zostanie poproszony przez IDE. Gdy IDE sprawia, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] że żądanie, z kolei spróbuje uzyskać ten interfejs z aktualnie zarejestrowanego formantu źródła VSPackage. Jeśli interfejs istnieje w zarejestrowanym VSPackage, żądanie IDE dla niestandardowych glifów powiedzie się; w przeciwnym [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] razie IDE używa domyślnego zestawu glifów.

 Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> jest używana [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przez do uzyskania listy obrazów przedstawiających różne stany kontroli źródła. Formant źródła VSPackage zwraca do IDE dojście do listy obrazów dla jego niestandardowych glifów. IDE tworzy kopię listy obrazów w tym momencie i używa go później, aby wybrać glify do wyświetlenia. Jeśli nowy interfejs nie jest `IVsSccGlyphs::GetCustomGlyphList` obsługiwany `E_NOTIMPL`lub metoda zwraca , ide pobiera jego glify z domyślnej listy glifów dostarczonych przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
