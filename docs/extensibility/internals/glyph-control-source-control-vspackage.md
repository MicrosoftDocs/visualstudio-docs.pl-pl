---
title: Kontrola symboli (pakiet VSPackage kontroli) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e432e045a55593f0967c7805323785cfc6acaa7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870050"
---
# <a name="glyph-control-source-control-vspackage"></a>Kontrola symboli (kontroli źródła pakietu VSPackage)
Głęboka integracja dostępne dla pakietów VSPackage kontroli źródła jest możliwość wyświetlania własne symbole w celu wskazania stanu elementów pod kontrolą źródła.  
  
## <a name="levels-of-glyph-control"></a>Poziomy kontrola symboli  
 Symbol stanu znajduje się ikona, który wskazuje bieżący stan elementem, gdy jest wyświetlana, na przykład w **Eksploratora rozwiązań** lub **Widok klas**. Pakietu VSPackage kontroli źródła można wykonywać dwa poziomy kontrola symboli. Można ograniczyć, wybór symbole do zestawu wstępnie zdefiniowane symbole dostarczone przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska IDE lub można zdefiniować niestandardowy zestaw symbole, które mają być wyświetlane.  
  
### <a name="default-set-of-glyphs"></a>Domyślny zestaw glifów  
 Aby określić stan symbole, które są skojarzone z elementem w **Eksploratora rozwiązań**, projekt żąda symbol stanu z kontroli źródła przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>. Kontroli źródła pakietu VSPackage może zadecydować, aby zachować wybór symbole ograniczone do wstępnie zdefiniowane symbole dostarczane przez środowisko IDE. W tym przypadku pakietu VSPackage odsyła tablicę wartości reprezentujący Symbol wyliczenia, które są zdefiniowane w *vsshell.idl*. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Jest to zestaw wstępnie zdefiniowanych symbole ustawione przez środowisko IDE, takie jak kłódka glifu zaewidencjonowania i znacznik wyboru glifu wyewidencjonowany.  
  
### <a name="custom-set-of-glyphs"></a>Niestandardowy zestaw glifów  
 Pakietu VSPackage kontroli źródła może na użytek własny symbole unikatowy wygląd i działanie po jej zainstalowaniu. W przypadku nowego pakietu VSPackage kontroli źródła jest aktywna, powinno być możliwe jej uruchomienie, przy użyciu własnej symbole, nawet jeśli pakietu VSPackage kontroli poprzedniego źródła nadal jest załadowany, ale nieaktywne. W tym trybie kontroli źródła pakietu VSPackage nadal można użyć istniejącej ikony utrzymane, gdy się spójne z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Jeśli zdecyduje się je.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> Usługi obsługuje interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, który pakietu VSPackage może opcjonalnie zaimplementować i który będzie wymagane podanie IDE. Gdy środowisko IDE zgłasza żądanie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] z kolei będą próbować pobierać ten interfejs z kontroli źródła obecnie zarejestrowaną pakietu VSPackage. Interfejs znajduje się w zarejestrowanej pakietu VSPackage, żądanie środowiska IDE dla niestandardowych symbole zakończy się pomyślnie; w przeciwnym razie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE używa domyślny zbiór symbole.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> Metoda jest używana przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stwierdza, aby uzyskać listę obrazy przedstawiające różne kontroli źródła. Kontrola źródła pakietu VSPackage zwraca środowiska IDE dojścia do listy obrazów do swojej niestandardowej symbole. IDE tworzy kopię listy obrazów w tym momencie i używa go później wybrać symbole do wyświetlenia. Jeśli nie jest obsługiwana przez nowy interfejs lub `IVsSccGlyphs::GetCustomGlyphList` metoda zwraca `E_NOTIMPL`, a następnie IDE pobiera jego symbole z domyślną listę symbole dostarczonych przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>