---
title: 'Jak: Wdrażanie projektów zagnieżdżonych | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d9dfe567db0b8788b93b13aeb760d45f4c05b57
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707985"
---
# <a name="how-to-implement-nested-projects"></a>Jak: Wdrażanie projektów zagnieżdżonych

Podczas tworzenia zagnieżdżonego typu projektu, istnieje kilka dodatkowych kroków, które muszą być zaimplementowane. Projekt nadrzędny przyjmuje niektóre z tych samych obowiązków, które rozwiązanie ma dla swoich projektów zagnieżdżonych (podrzędnych). Projekt nadrzędny jest kontenerem projektów podobnych do rozwiązania. W szczególności istnieje kilka zdarzeń, które muszą być wywoływane przez rozwiązanie i przez projekty nadrzędne do tworzenia hierarchii projektów zagnieżdżonych. Zdarzenia te są opisane w następującym procesie tworzenia projektów zagnieżdżonych.

## <a name="create-nested-projects"></a>Tworzenie projektów zagnieżdżonych

1. Zintegrowane środowisko programistyczne (IDE) ładuje plik projektu projektu nadrzędnego i informacje o starcie, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfejs. Projekt nadrzędny jest tworzony i dodawany do rozwiązania.

    > [!NOTE]
    > W tym momencie jest zbyt wcześnie w procesie dla projektu nadrzędnego, aby utworzyć projekt zagnieżdżony, ponieważ projekt nadrzędny musi zostać utworzony przed tworzenie projektów podrzędnych. Po tej sekwencji projekt nadrzędny można zastosować ustawienia do projektów podrzędnych i projekty podrzędne mogą uzyskać informacje z projektów nadrzędnych w razie potrzeby. Ta sekwencja jest, jeśli jest to wymagane przez klientów, takich jak kontrola kodu źródłowego (SCC) i **Eksplorator rozwiązań.**

     Projekt nadrzędny musi <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> czekać na metodę, która ma być wywoływana przez IDE, zanim będzie można utworzyć jego zagnieżdżone (podrzędne) projektu lub projektów.

2. IDE wywołuje `QueryInterface` projekt nadrzędny <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>dla . Jeśli to wywołanie powiedzie <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> się, IDE wywołuje metodę nadrzędnego, aby otworzyć wszystkie projekty zagnieżdżone dla projektu nadrzędnego.

3. Projekt nadrzędny <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> wywołuje metodę powiadamiania detektorów, że projekty zagnieżdżone mają zostać utworzone. SCC, na przykład, nasłuchuje tych zdarzeń, aby wiedzieć, czy kroki w procesie tworzenia rozwiązania i projektu występują w kolejności. Jeśli kroki wystąpią poza kolejnością, rozwiązanie może nie być poprawnie zarejestrowane z kontrolą kodu źródłowego.

4. Projekt nadrzędny <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> metodę lub metodę w każdym z jego projektów podrzędnych.

     Należy <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> przekazać `AddVirtualProject` do metody, aby wskazać, że projekt wirtualny (zagnieżdżone) powinny być dodawane do okna projektu, wyłączone z kompilacji, dodane do kontroli kodu źródłowego i tak dalej. `VSADDVPFLAGS`pozwala kontrolować widoczność zagnieżdżonego projektu i wskazać, jakie funkcje są z nim skojarzone.

     W przypadku ponownego załadowania wcześniej istniejącego projektu podrzędnego, w którego identyfikator GUID projektu `AddVirtualProjectEx`jest przechowywany w pliku projektu nadrzędnego, projekt nadrzędny wywołuje . Jedyną `AddVirtualProject` różnicą `AddVirtualProjectEX` między `AddVirtualProjectEX` i jest to, że ma parametr, aby umożliwić projekt nadrzędny, aby określić na wystąpienie `guidProjectID` dla projektu podrzędnego, aby włączyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> działać poprawnie.

     Jeśli nie ma dostępnego identyfikatora GUID, na przykład podczas dodawania nowego projektu zagnieżdżonego, rozwiązanie tworzy jeden dla projektu w momencie dodania go do obiektu nadrzędnego. Jest odpowiedzialny za projekt nadrzędny do utrwalenia tego identyfikatora GUID projektu w pliku projektu. Jeśli usuniesz projekt zagnieżdżony, identyfikator GUID dla tego projektu można również usunąć.

5. IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> metodę na każdym projekcie podrzędnym projektu nadrzędnego.

     Projekt nadrzędny `IVsParentProject` musi zostać zaimplementowany, jeśli chcesz zagnieżdżać projekty. Ale projekt nadrzędny `QueryInterface` `IVsParentProject` nigdy nie wymaga, nawet jeśli ma projekty nadrzędne pod nim. Rozwiązanie obsługuje wywołanie `IVsParentProject` do i, jeśli jest `OpenChildren` zaimplementowana, wywołania utworzenia projektów zagnieżdżonych. `AddVirtualProjectEX`jest zawsze `OpenChildren`wywoływana z . Nigdy nie powinny być wywoływane przez projekt nadrzędny, aby zachować zdarzenia tworzenia hierarchii w porządku.

6. IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> metodę w projekcie podrzędnym.

7. Projekt nadrzędny <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> wywołuje metodę powiadamiania odbiorników, że projekty podrzędne dla nadrzędnego zostały utworzone.

8. IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> metodę w projekcie nadrzędnym po otwarciu wszystkich projektów podrzędnych.

     Jeśli jeszcze nie istnieje, projekt nadrzędny tworzy identyfikator GUID `CoCreateGuid`dla każdego projektu zagnieżdżonego przez wywołanie .

    > [!NOTE]
    > `CoCreateGuid`jest interfejsem API COM wywoływanym podczas tworzenia identyfikatora GUID. Aby uzyskać więcej `CoCreateGuid` informacji, zobacz guids w bibliotece MSDN.

     Projekt nadrzędny przechowuje ten identyfikator GUID w pliku projektu do pobrania przy następnym otwarciu w IDE. Zobacz krok 4, aby uzyskać więcej `AddVirtualProjectEX` informacji dotyczących `guidProjectID` wywoływania, aby pobrać dla projektu podrzędnego.

9. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> jest następnie wywoływana dla nadrzędnego ItemID, który zgodnie z konwencją można delegować do projektu zagnieżdżonego. Pobiera <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> właściwości węzła, który zagnieżdża projekt, który chcesz delegować, gdy jest wywoływana na element nadrzędny.

     Ponieważ projekty nadrzędne i podrzędne są tworzone programowo programowo, można ustawić właściwości dla projektów zagnieżdżonych w tym momencie.

    > [!NOTE]
    > Nie tylko otrzymujesz informacje kontekstowe z projektu zagnieżdżonego, ale można również zapytać, czy projekt nadrzędny ma dowolny kontekst dla tego elementu, sprawdzając [__VSHPROPID. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). W ten sposób można dodać dodatkowe dynamiczne atrybuty pomocy i opcje menu specyficzne dla poszczególnych projektów zagnieżdżonych.

10. Hierarchia jest przeznaczona do wyświetlania w <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> **Eksploratorze rozwiązań** z wywołaniem metody.

     Przekazujesz hierarchię do środowiska, aby utworzyć `GetNestedHierarchy` hierarchię do wyświetlenia w Eksploratorze rozwiązań. W ten sposób rozwiązanie wie, że projekt istnieje i może być zarządzany do tworzenia przez menedżera kompilacji lub może zezwolić na pliki w projekcie, które mają być poddane kontroli kodu źródłowego.

11. Po utworzeniu wszystkich projektów zagnieżdżonych dla programu Project1 kontrola jest przekazywana z powrotem do rozwiązania, a proces jest powtarzany dla programu Project2.

     Ten sam proces tworzenia projektów zagnieżdżonych występuje dla projektu podrzędnego, który ma podrzędny. W takim przypadku jeśli BuildProject1, który jest elementem podrzędnym Project1, miał projekty podrzędne, zostaną one utworzone po BuildProject1 i przed Project2. The process is recursive and the hierarchy is built from the top down.

     Gdy projekt zagnieżdżony jest zamknięty, ponieważ użytkownik zamknął rozwiązanie `IVsParentProject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>lub sam konkretny projekt, wywoływana jest inna metoda na , . Projekt nadrzędny zawija <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> z i metody powiadamiania odbiorników do zdarzeń rozwiązania, które są zamykane projekty zagnieżdżone.

Następujące tematy dotyczą kilku innych pojęć, które należy wziąć pod uwagę podczas wdrażania projektów zagnieżdżonych:

- [Zagadnienia dotyczące rozładunku i przeładunku projektów zagnieżdżonych](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Obsługa kreatora dla projektów zagnieżdżonych](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Wdrażanie obsługi poleceń dla projektów zagnieżdżonych](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrowanie okna dialogowego AddItem dla projektów zagnieżdżonych](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Zobacz też

- [Dodawanie elementów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Rejestrowanie szablonów projektów i towarów](../../extensibility/internals/registering-project-and-item-templates.md)
- [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parametry kontekstu](../../extensibility/internals/context-parameters.md)
- [Plik Kreatora (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
