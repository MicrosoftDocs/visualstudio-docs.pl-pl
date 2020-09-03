---
title: Zarządzanie posiadaczami blokady dokumentu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73c6151b5c02cb81a10c2725091c16457db70e33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204638"
---
# <a name="document-lock-holder-management"></a>Zarządzanie właścicielem blokady dokumentu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W uruchomionej tabeli dokumentu (RDT) jest przechowywana liczba otwartych dokumentów i wszelkich zabloków edycji, które mają. Możesz umieścić blokadę edycji dokumentu w RDT, gdy jest on programowo edytowany w tle bez wyświetlania otwartego dokumentu w oknie dokumentu. Ta funkcja jest często używana przez projektantów, którzy modyfikują wiele plików za pomocą graficznego interfejsu użytkownika.  
  
## <a name="document-lock-holder-scenarios"></a>Scenariusze dotyczące posiadaczy blokady dokumentu  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>Plik "a" ma zależność od pliku "b"  
 Rozważmy sytuację, w której zaimplementowano standardowy Edytor "A" dla typu pliku "a", a każdy plik typu "a" ma odwołanie do pliku typu "b", który jest zależny od tego. Standardowy Edytor "B" istnieje dla plików typu "b". Gdy Edytor "A" otwiera plik "a", pobiera odwołanie do odpowiedniego pliku "b". Plik "b" nie jest wyświetlany, ale Edytor "A" może go zmodyfikować. Edytor "A" uzyskuje odwołanie do danych dokumentu pliku "b" z <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metody, a także zachowuje blokadę edycji pliku "b". Po zakończeniu modyfikacji pliku "b" przez Edytor "A" można zmniejszyć liczbę blokad edycji dla pliku "b", wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> metodę. Możesz pominąć ten krok, jeśli metoda została wywołana <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> z parametrem `dwRDTLockType` ustawionym na <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> .  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>Plik "b" jest otwarty przez inny edytor  
 W przypadku, gdy plik "b" jest już otwarty przez Edytor "B", gdy Edytor "A" próbuje go otworzyć, istnieją dwa oddzielne scenariusze do obsłużenia:  
  
- Jeśli plik "b" jest otwarty w zgodnym edytorze, musisz mieć edytora "A", aby zarejestrować plik "b" przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metody. Po zmodyfikowaniu pliku "b" przez Edytor "A" Wyrejestruj blokadę edycji dokumentu przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> metody.  
  
- Jeśli plik "b" jest otwarty w niezgodny sposób, można pozwolić na próbę otwarcia pliku "b" przez Edytor "A" Niepowodzenie lub można zezwolić na widok skojarzony z edytorem "A" częściowo otwartym i wyświetlającym odpowiedni komunikat o błędzie. Komunikat o błędzie powinien spowodować, że użytkownik zamknie plik "b" w niezgodnym edytorze, a następnie ponownie otworzy plik "a" przy użyciu edytora "A". Możesz również zaimplementować metodę, [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> Aby monitować użytkownika o zamknięcie pliku "b", który jest otwarty w niezgodnym edytorze. Jeśli użytkownik zamknie plik "b", otwieranie pliku "a" w edytorze "A" zwykle kontynuuje się.  
  
## <a name="additional-document-edit-lock-considerations"></a>Dodatkowe zagadnienia dotyczące blokady edycji dokumentu  
 Jest możliwe inne zachowanie, jeśli edytor "A" jest jedynym edytorem, który ma blokadę edycji dokumentu w pliku "b", niż w przypadku, gdy Edytor "B" także przechowuje blokadę dokumentu w pliku "b". W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] programie **Projektant klas** to przykład projektanta wizualnego, który nie utrzymuje blokady edycji w skojarzonym pliku kodu. Oznacza to, że jeśli użytkownik ma otwarty Diagram klas w widoku projektu, a skojarzony plik kodu jest otwarty jednocześnie, a użytkownik modyfikuje plik kodu, ale nie zapisze zmian, zmiany zostaną również utracone do pliku diagramu klasy (. CD). Jeśli **Projektant klas** ma tylko blokadę edycji dokumentu w pliku kodu, użytkownik nie będzie monitowany o zapisanie zmian podczas zamykania pliku kodu. IDE prosi użytkownika o zapisanie zmian dopiero po zamknięciu **Projektant klas**przez użytkownika. Zapisane zmiany są odzwierciedlone w obu plikach. Jeśli zarówno **Projektant klas** , jak i edytor plików kodu zachowały edycję dokumentu w pliku kodu, użytkownik zostanie poproszony o zapisanie podczas zamykania pliku kodu lub formularza. W tym momencie zapisane zmiany są odzwierciedlone zarówno w formularzu, jak i w pliku kodu. Aby uzyskać więcej informacji na diagramach klas, zobacz [Praca z diagramami klas (Projektant klas)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Należy pamiętać, że jeśli trzeba umieścić blokadę edycji dokumentu dla programu bez edytora, należy zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfejs.  
  
 Wiele razy Projektant interfejsu użytkownika, który modyfikuje pliki kodu programowo, wprowadza zmiany w więcej niż jednym pliku. W takich przypadkach <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> Metoda obsługuje zapisywanie w jednym lub kilku dokumentach przy użyciu **czy chcesz zapisać zmiany w następujących elementach?** okna dialogowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchamianie tabeli dokumentu](../extensibility/internals/running-document-table.md)   
 [Trwałość i uruchamianie tabeli dokumentów](../extensibility/internals/persistence-and-the-running-document-table.md)
