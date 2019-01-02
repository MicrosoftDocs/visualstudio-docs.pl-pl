---
title: Decyzje projektowe dotyczące kontroli źródła | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd1ffa27a8dfa7c1d98e7242d71f7cfe83c319d4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883188"
---
# <a name="source-control-design-decisions"></a>Decyzje projektowe dotyczące kontroli kodu źródłowego
Podczas implementowania kontroli źródła należy rozważyć następujące decyzje dotyczące projektu dla projektów.  
  
## <a name="will-information-be-shared-or-private"></a>Informacje będą współużytkowany lub prywatny?  
 Najważniejsza decyzja projektowa, możesz wprowadzić to, jakie informacje są zabezpieczać i co to jest prywatna. Na przykład lista plików dla projektu jest udostępniany, ale w ramach tej listy plików, niektórzy użytkownicy może być wskazane pliki prywatne. Ustawienia kompilatora są udostępniane, ale projektu startowego jest zwykle oznaczony jako prywatny. Ustawienia są wyłącznie udostępnione, udostępnione za pomocą zastąpienia lub czysto prywatnych. Zgodnie z projektem, prywatne elementy, takie jak rozwiązania użytkownika opcje plików (suo) nie są sprawdzane w [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]. Należy przechowywać poufnych informacji w plikach prywatnych, takich jak plik .suo lub określonego pliku prywatnego, tworzenia, np. plik csproj.user dla języka Visual C# lub. plik vbproj.user dla języka Visual Basic.  
  
 Ta decyzja nie jest kompleksowych i mogą być wykonane na podstawie elementu —.  
  
## <a name="will-the-project-include-special-files"></a>Projekt zawierają specjalne pliki?  
 Inny decyzja projektowa ważne jest, czy do struktury projektu używa specjalne pliki. Specjalne pliki są ukryte pliki, które opierają się pliki, które są widoczne w Eksploratorze rozwiązań i zaewidencjonowania i wyewidencjonowania okien dialogowych. Jeśli używasz specjalnych plików, należy przestrzegać następujących wytycznych:  
  
1.  Nie należy kojarzyć specjalne pliki z głównego węzła projektu — oznacza to, z projektem samego pliku. Plik projektu musi być pojedynczy plik.  
  
2.  Gdy specjalne pliki są dodane, usunięte lub zmieniono jego nazwę w projekcie w języku odpowiednim <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> zdarzenia musi być uruchamiane z ustawioną flagą wskazującą są specjalne pliki. Te zdarzenia są wywoływane przez środowisko w odpowiedzi na projekt wywołanie odpowiedniego <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> metody.  
  
3.  Kiedy wywołuje swój projekt lub edytor <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> dla pliku, specjalne pliki skojarzone z tym plikiem nie zostały automatycznie wyewidencjonowane. Przekaż specjalne pliki w wraz z plikiem nadrzędnym. Środowisko wykryje relacji między wszystkie pliki, które są przekazywane w i odpowiednio Ukryj specjalne pliki w Interfejsie użytkownika wyewidencjonowywania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)