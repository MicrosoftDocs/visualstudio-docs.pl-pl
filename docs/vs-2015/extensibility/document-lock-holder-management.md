---
title: Zarządzanie właścicielem blokady dokumentu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8eaeb8529f570db112bf43813fe20339f3bca7c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786304"
---
# <a name="document-lock-holder-management"></a>Zarządzanie właścicielem blokady dokumentu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tabela systemem dokumentu (Normalizacją) przechowuje liczbę otwartych dokumentów i wszystkie blokady edycji, które mają. Można umieścić blokady edycji dokumentu w Normalizacją, gdy programowe jest edytowany w tle bez użytkownika wyświetlany w oknie dokumentu otwartego dokumentu. Ta funkcja jest często używane przez projektantów, które modyfikują wiele plików za pomocą graficznego interfejsu użytkownika.  
  
## <a name="document-lock-holder-scenarios"></a>Scenariusze właściciela blokady dokumentu  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>Plik "" jest już zależny od pliku "b"  
 Rozważmy sytuację, w którym implementuje Edytor standardowy "A" dla typu pliku "a", a następnie każdego pliku, typu "" zawiera odwołanie do (lub ma znaczenie) pliku typu "b". Edytor standardowy "B" nie istnieje dla plików typu "b". Gdy plik jest otwierany w edytorze "A" "" it pobiera odwołanie do odpowiedniego pliku "b". Plik "b" nie jest wyświetlana, ale można go zmodyfikować, Edytor "A". Edytor "A" uzyskuje odwołanie do danych dokumentu z pliku "b" z <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metody i udostępnia również Edytuj blokadę pliku "b". Po zakończeniu edytora "A" modyfikowania pliku "b", można zmniejszyć blokady edycji liczyć na w pliku "b", wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> metody. Możesz pominąć ten krok, jeśli były nazywane <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metody z parametrem `dwRDTLockType` równa <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>Plik "b" jest otwarty przez inny edytor  
 W przypadku, gdy plik "b" jest już otwarty przez Edytor "B", gdy spróbuje go otworzyć w edytorze "A", istnieją dwa scenariusze oddzielnych do obsługi:  
  
-   Jeśli plik "b" jest otwarty w edytorze zgodne, konieczne jest posiadanie edytora "A" Zarejestruj blokadę edycji dokumentów na temat korzystania z pliku "b" <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metody. Po wykonaniu czynności modyfikowania pliku "b" w edytorze "A", dokument wyrejestrować Edytuj przy użyciu blokady <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> metody.  
  
-   Jeśli plik "b" jest otwarty w sposób niezgodny, można albo pozwolić próba otwarcia pliku "b", przez Edytor "" Niepowodzenie, lub można pozwolić, aby widok skojarzone z edytorem "A" częściowo otworzyć i wyświetlić odpowiedni komunikat o błędzie. Komunikat o błędzie powinien Poinstruuj użytkownika, aby zamknąć pliku "b" w niezgodnym edytorze, a następnie ponownie otwórz plik "a" przy użyciu edytora "A". Możesz również wdrożyć [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> na monitowanie użytkownika można zamknąć pliku "b", który jest otwarty w niezgodnym edytorze. Jeśli użytkownik zamknie pliku "b", otwierania pliku "" w edytorze "A" nadal normalnie.  
  
## <a name="additional-document-edit-lock-considerations"></a>Zagadnienia dotyczące blokowania edycji dodatkową dokumentów  
 Możesz uzyskać różne zachowanie, jeśli edytor "A" jest tylko edytor, który zawiera dokument, Edytuj blokadę dla pliku "b", niż w przypadku, jeśli edytor "B" również zawiera dokument Edytuj blokadę dla pliku "b". W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], **projektanta klas** jest przykładem projektanta wizualnego, który nie posiada blokady edycji w pliku skojarzonego kodu. Oznacza to jeśli użytkownik ma diagramu klas, Otwórz w widoku Projekt, a jednocześnie można otworzyć pliku skojarzonego kodu, a użytkownik modyfikuje plik kodu, ale nie do zapisania zmian, zmiany są również utraci plik diagramu klasy (.cd). Jeśli **projektanta klas** ma tylko dokumentu edytować blokady o plik kodu, użytkownik nie będzie monitowany zapisanie zmian podczas zamykania pliku kodu. Środowisko IDE z monitem o zapisanie zmian tylko w przypadku, gdy użytkownik zamknie **projektanta klas**. Zapisano zmiany są odzwierciedlane w obu plikach. Jeśli oba **projektanta klas** i Edytor kodu w pliku posiadanych blokad edycji dokumentu w pliku kodu, a następnie użytkownik jest monitowany zapisywane podczas zamykania pliku z kodem lub formularzu. W tym momencie zapisane zmiany są odzwierciedlane w formularzu i pliku kodu. Aby uzyskać więcej informacji dotyczących diagramów klas, zobacz [Praca z diagramami klas (Projektant klas)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Należy pamiętać, że jeśli zachodzi potrzeba zablokować edycji dokumentu bez edytora, należy zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfejsu.  
  
 Wiele razy z interfejsu użytkownika projektanta programowo modyfikuje pliki kodu zmienia więcej niż jeden plik. W takich przypadkach <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> obsługiwała zapisywania dokumentów, poprzez **czy chcesz zapisać zmiany w następujących elementach?** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchamianie tabeli dokumentu](../extensibility/internals/running-document-table.md)   
 [Trwałość i uruchamianie tabeli dokumentów](../extensibility/internals/persistence-and-the-running-document-table.md)

