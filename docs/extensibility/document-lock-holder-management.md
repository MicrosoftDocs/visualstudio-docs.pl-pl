---
title: Zarządzanie posiadaczami blokad dokumentów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9dd520f8ad5cab1f0cfee890c4bcc388c204bb1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712128"
---
# <a name="document-lock-holder-management"></a>Zarządzanie posiadaczami blokady dokumentów

Uruchomiona tabela dokumentów (RDT) przechowuje liczbę otwartych dokumentów i blokad edycji, które mają. Blokadę edycji można umieścić w dokumencie w dokumencie RDT, gdy jest on programowo edytowany w tle bez wyświetlania otwartego dokumentu w oknie dokumentu. Ta funkcja jest często używana przez projektantów, którzy modyfikują wiele plików za pośrednictwem graficznego interfejsu użytkownika.

## <a name="document-lock-holder-scenarios"></a>Scenariusze posiadaczy blokady dokumentu

### <a name="file-a-has-a-dependence-on-file-b"></a>Plik "a" jest zależny od pliku "b"

Należy wziąć pod uwagę sytuację, w której zaimplementujesz standardowy edytor "A" dla typu pliku "a", a każdy plik typu "a" ma odwołanie do pliku typu "b" lub zależność od tego pliku. Standardowy edytor "B" istnieje dla plików typu "b". Gdy edytor "A" otwiera plik "a" pobiera odwołanie do odpowiedniego pliku "b". Plik "b" nie jest wyświetlany, ale edytor "A" może go zmodyfikować. Edytor "A" uzyskuje odniesienie do danych dokumentu pliku "b" z <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metody, a także utrzymuje blokadę edycji w pliku "b". Po edytorze "A" jest wykonywana modyfikowanie pliku "b" można zdekstrować <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> liczbę blokady edycji na plik "b", wywołując metodę. Ten krok można pominąć, jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metoda została `dwRDTLockType` wywołana z parametrem ustawionym na [_VSRDTFLAGS. RDT_NoLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>).

### <a name="file-b-is-opened-by-a-different-editor"></a>Plik "b" jest otwierany przez inny edytor

W przypadku, gdy plik "b" jest już otwarty przez edytor "B", gdy edytor "A" próbuje go otworzyć, istnieją dwa oddzielne scenariusze do obsługi:

- Jeśli plik "b" jest otwarty w zgodnym edytorze, musisz mieć edytor "A" <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> zarejestrować blokadę edycji dokumentu w pliku "b" przy użyciu metody. Po edytorze "A" jest wykonywana modyfikowanie pliku "b", odblokuj blokadę edycji dokumentu przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> metody.

- Jeśli plik "b" jest otwarty w sposób niezgodny, można pozwolić, aby próba otwarcia pliku "b" przez edytor "A" nie powiodła się, lub można pozwolić widok skojarzony z edytorem "A" częściowo otworzyć i wyświetlić odpowiedni komunikat o błędzie. Komunikat o błędzie powinien poinstruować użytkownika, aby zamknąć plik "b" w niekompatybilnym edytorze, a następnie ponownie otworzyć plik "a" za pomocą edytora "A". Można również zaimplementować [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> monitowania użytkownika o zamknięcie pliku "b", który jest otwarty w niekompatybilnym edytorze. Jeśli użytkownik zamknie plik "b", otwarcie pliku "a" w edytorze "A" będzie kontynuowane normalnie.

## <a name="additional-document-edit-lock-considerations"></a>Dodatkowe zagadnienia dotyczące blokady edycji dokumentu

Otrzymujesz inne zachowanie, jeśli edytor "A" jest jedynym edytorem, który ma blokadę edycji dokumentu w pliku "b" niż w przypadku edytora "B" posiada również blokadę edycji dokumentu w pliku "b". W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]programie **Projektant klas** jest przykładem projektanta wizualnego, który nie posiada blokady edycji skojarzonego pliku kodu. Oznacza to, że jeśli użytkownik ma diagram klasy otwarty w widoku projektu i skojarzony plik kodu otwarty jednocześnie, a użytkownik modyfikuje plik kodu, ale nie zapisuje zmian, zmiany są również tracone do pliku diagramu klasy (.cd). Jeśli **Projektant klasy** ma tylko blokady edycji dokumentu w pliku kodu, użytkownik nie jest proszony o zapisanie zmian podczas zamykania pliku kodu. IDE prosi użytkownika, aby zapisać zmiany dopiero po użytkownik zamyka **Projektanta klas**. Zapisane zmiany zostaną odzwierciedlone w obu plikach. Jeśli zarówno **Projektant klasy,** jak i edytor dokumentów przechowywane w kodzie edytują dokument, zostanie wyświetlony monit o zapisanie podczas zamykania pliku kodu lub formularza. W tym momencie zapisane zmiany są odzwierciedlane zarówno w formularzu, jak i w pliku kodu. Aby uzyskać więcej informacji na temat diagramów klas, zobacz [Praca z diagramami klas (Projektant klas)](../ide/class-designer/designing-and-viewing-classes-and-types.md).

Należy zauważyć, że jeśli chcesz umieścić blokadę edycji w dokumencie <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> dla nienajedyny, należy zaimplementować interfejs.

Wiele razy projektant interfejsu użytkownika, który modyfikuje pliki kodu programowo wprowadza zmiany do więcej niż jednego pliku. W takich <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> przypadkach metoda obsługuje zapisywanie jednego lub więcej dokumentów za pomocą **czy chcesz zapisać zmiany w następujących elementach?**

## <a name="see-also"></a>Zobacz też

- [Uruchamianie tabeli dokumentów](../extensibility/internals/running-document-table.md)
- [Trwałość i bieżąca tabela dokumentów](../extensibility/internals/persistence-and-the-running-document-table.md)
