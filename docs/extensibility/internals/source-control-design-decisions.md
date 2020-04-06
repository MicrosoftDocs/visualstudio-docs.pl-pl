---
title: Decyzje dotyczące projektowania kontroli źródeł | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c36bb2b50a72a52aeaeb7712f4ed711845b5e6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705244"
---
# <a name="source-control-design-decisions"></a>Decyzje projektowe dotyczące kontroli kodu źródłowego
Następujące decyzje dotyczące projektu powinny być brane pod uwagę dla projektów podczas wdrażania kontroli źródła.

## <a name="will-information-be-shared-or-private"></a>Czy informacje będą udostępniane, czy prywatne?
 Najważniejszą decyzją projektową, jaką możesz podjąć, jest to, jakie informacje można udostępniać, a co prywatne. Na przykład lista plików dla projektu jest udostępniana, ale na tej liście plików niektórzy użytkownicy mogą chcieć mieć pliki prywatne. Ustawienia kompilatora są współużytkowane, ale projekt rozruchowy jest zazwyczaj prywatny. Ustawienia są albo czysto współużytkowane, współużytkowane z zastąpieniem lub czysto prywatne. Zgodnie z projektem elementy prywatne, takie jak pliki opcji użytkownika rozwiązania [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)](.suo), nie są zaewidencjonowane w pliku . Pamiętaj, aby przechowywać wszelkie prywatne informacje w plikach prywatnych, takich jak plik .suo lub określony plik prywatny, który tworzysz, na przykład plik csproj.user dla języka Visual C# lub plik .vbproj.user dla języka Visual Basic.

 Decyzja ta nie jest all-inclusive i mogą być podejmowane na podstawie pozycji po elemencie.

## <a name="will-the-project-include-special-files"></a>Czy projekt będzie zawierał pliki specjalne?
 Inną ważną decyzją projektową jest to, czy struktura projektu używa plików specjalnych. Pliki specjalne to ukryte pliki, które stanowią podstawę plików widocznych w Eksploratorze rozwiązań oraz w oknach dialogowych zaewidencjonowania i wyewidencjonowywaniem. Jeśli używasz plików specjalnych, postępuj zgodnie z tymi wskazówkami:

1. Nie należy kojarzyć plików specjalnych z węzłem głównym projektu — to znaczy z samym plikiem projektu. Plik projektu musi być pojedynczym plikiem.

2. Po dodaniu, usunięciu lub zmianie nazwy plików w <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> projekcie odpowiednie zdarzenia muszą zostać odwołane z zestawem flag wskazujących, że pliki są plikami specjalnymi. Zdarzenia te są wywoływane przez środowisko w <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> odpowiedzi na projekt wywołując odpowiednie metody.

3. Gdy projekt lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> edytor wymaga pliku, pliki specjalne skojarzone z tym plikiem nie są automatycznie wyewidencjonowywane. Przekaż pliki specjalne wraz z plikiem nadrzędnym. Środowisko wykryje relację między wszystkimi plikami, które są przekazywane i odpowiednio ukryć pliki specjalne w interfejsie użytkownika wyewidencjonowania.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)
