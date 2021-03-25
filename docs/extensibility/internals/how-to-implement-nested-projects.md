---
title: 'Instrukcje: implementowanie projektów zagnieżdżonych | Microsoft Docs'
description: Dowiedz się, jak zaimplementować zagnieżdżone projekty w programie Visual Studio, wywołując zdarzenia z rozwiązania i projektów nadrzędnych w celu utworzenia hierarchii projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 49f2e3b971c16b63f900424aa99649e424490d30
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078867"
---
# <a name="how-to-implement-nested-projects"></a>Instrukcje: implementowanie projektów zagnieżdżonych

Gdy tworzysz zagnieżdżony typ projektu, istnieje kilka dodatkowych kroków, które należy zaimplementować. Projekt nadrzędny przyjmuje niektóre z tych samych obowiązków, które rozwiązanie ma w przypadku projektów zagnieżdżonych (podrzędnych). Projekt nadrzędny jest kontenerem projektów podobnych do rozwiązania. W szczególności istnieje kilka zdarzeń, które muszą zostać zgłoszone przez rozwiązanie i projekty nadrzędne, aby utworzyć hierarchię zagnieżdżonych projektów. Te zdarzenia są opisane w poniższym procesie tworzenia zagnieżdżonych projektów.

## <a name="create-nested-projects"></a>Tworzenie zagnieżdżonych projektów

1. Zintegrowane środowisko programistyczne (IDE) ładuje plik projektu i informacje uruchomieniowe projektu nadrzędnego przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfejsu. Projekt nadrzędny jest tworzony i dodawany do rozwiązania.

    > [!NOTE]
    > W tym momencie jest zbyt wczesny w procesie dla projektu nadrzędnego, aby utworzyć zagnieżdżony projekt, ponieważ należy utworzyć projekt nadrzędny, aby można było utworzyć projekty podrzędne. Po tej sekwencji projekt nadrzędny może zastosować ustawienia do projektów podrzędnych, a projekty podrzędne mogą uzyskać informacje z projektów nadrzędnych, jeśli jest to konieczne. Ta sekwencja jest wymagana w przypadku klientów, takich jak kontrola kodu źródłowego (SCC) i **Eksplorator rozwiązań**.

     Projekt nadrzędny musi czekać, aż <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> Metoda zostanie wywołana przez IDE, zanim będzie mogła utworzyć zagnieżdżony (podrzędny) projekt lub projekty.

2. IDE wywołuje `QueryInterface` w projekcie nadrzędnym dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject> . Jeśli to wywołanie powiedzie się, IDE wywoła <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> metodę elementu nadrzędnego, aby otworzyć wszystkie zagnieżdżone projekty dla projektu nadrzędnego.

3. Projekt nadrzędny wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> metodę w celu powiadomienia detektorów, które mają zostać utworzone przez projekty zagnieżdżone. SCC, na przykład, nasłuchuje na tych zdarzeniach, aby dowiedzieć się, czy kroki w rozwiązaniu i procesie tworzenia projektu są wykonywane w określonej kolejności. Jeśli kroki wystąpiły poza kolejnością, rozwiązanie może nie być zarejestrowane z kontrolą kodu źródłowego.

4. Projekt nadrzędny wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> metodę lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> metodę dla każdego z jego projektów podrzędnych.

     Przekazujesz <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> do `AddVirtualProject` metody, aby wskazać, że wirtualny (zagnieżdżony) projekt powinien zostać dodany do okna projektu, wyłączony z kompilacji, dodany do kontroli kodu źródłowego i tak dalej. `VSADDVPFLAGS` pozwala kontrolować widoczność zagnieżdżonego projektu i wskazywać, jakie funkcje są z nią skojarzone.

     Jeśli załadujesz poprzednio istniejący projekt podrzędny, który ma identyfikator GUID projektu przechowywany w pliku projektu projektu nadrzędnego, nastąpiło wywołanie projektu nadrzędnego `AddVirtualProjectEx` . Jedyną różnicą między `AddVirtualProject` i `AddVirtualProjectEX` jest, która `AddVirtualProjectEX` ma parametr umożliwiający projektowi nadrzędnemu Określanie wystąpienia `guidProjectID` dla projektu podrzędnego w celu włączenia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> prawidłowego działania.

     Jeśli nie ma dostępnego identyfikatora GUID, na przykład podczas dodawania nowego projektu zagnieżdżonego, rozwiązanie tworzy jeden dla projektu w momencie dodania do obiektu nadrzędnego. Jest odpowiedzialny za projekt nadrzędny, aby zachować ten identyfikator GUID projektu w pliku projektu. Jeśli usuniesz zagnieżdżony projekt, można również usunąć identyfikator GUID dla tego projektu.

5. IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> metodę dla każdego projektu podrzędnego projektu nadrzędnego.

     Projekt nadrzędny musi być zaimplementowany, `IVsParentProject` Jeśli chcesz zagnieżdżać projekty. Ale projekt nadrzędny nigdy nie wywołuje się, `QueryInterface` `IVsParentProject` nawet jeśli zawiera projekty nadrzędne poniżej. Rozwiązanie obsługuje wywołanie do `IVsParentProject` i, jeśli jest zaimplementowane, wywołuje `OpenChildren` Tworzenie zagnieżdżonych projektów. `AddVirtualProjectEX` jest zawsze wywoływana z `OpenChildren` . Nie powinien być nigdy wywoływany przez projekt nadrzędny, aby zachować zdarzenia tworzenia hierarchii w kolejności.

6. IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> metodę w projekcie podrzędnym.

7. Projekt nadrzędny wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> metodę w celu powiadomienia detektorów o utworzeniu projektów podrzędnych dla elementu nadrzędnego.

8. IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> metodę w projekcie nadrzędnym po otwarciu wszystkich projektów podrzędnych.

     Jeśli jeszcze nie istnieje, projekt nadrzędny tworzy identyfikator GUID dla każdego zagnieżdżonego projektu przez wywołanie `CoCreateGuid` .

    > [!NOTE]
    > `CoCreateGuid` jest interfejsem API modelu COM wywoływanym, gdy zostanie utworzony identyfikator GUID. Aby uzyskać więcej informacji, zobacz `CoCreateGuid` i identyfikatory GUID w bibliotece MSDN.

     Projekt nadrzędny przechowuje ten identyfikator GUID w pliku projektu do pobrania przy następnym otwarciu w środowisku IDE. Zobacz Krok 4, aby uzyskać więcej informacji dotyczących wywoływania programu w `AddVirtualProjectEX` celu pobrania `guidProjectID` dla projektu podrzędnego.

9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>Metoda jest następnie wywoływana dla nadrzędnego elementu ItemId, który jest delegowany przez Konwencję w projekcie zagnieżdżonym. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>Pobiera właściwości węzła, który zagnieżdża projekt, w którym ma być delegowany, gdy jest wywoływana w obiekcie nadrzędnym.

     Ponieważ nadrzędne i podrzędne projekty są tworzone programowo, można ustawić właściwości dla zagnieżdżonych projektów w tym momencie.

    > [!NOTE]
    > Nie tylko otrzymujesz informacje kontekstowe z projektu zagnieżdżonego, ale możesz także zażądać, aby projekt nadrzędny miał kontekst dla tego elementu, sprawdzając [__VSHPROPID. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). W ten sposób można dodać dodatkowe atrybuty pomocy dynamicznej i opcje menu specyficzne dla pojedynczych zagnieżdżonych projektów.

10. Hierarchia jest skompilowana do wyświetlania w **Eksplorator rozwiązań** z wywołaniem <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> metody.

     Hierarchię można przekazać do środowiska za pomocą programu, `GetNestedHierarchy` Aby utworzyć hierarchię do wyświetlania w Eksplorator rozwiązań. W ten sposób rozwiązanie wie, że projekt istnieje i może być zarządzany do kompilowania przez Menedżera kompilacji lub można zezwolić na umieszczenie plików w projekcie pod kontrolą kodu źródłowego.

11. Po utworzeniu wszystkich zagnieżdżonych projektów dla Project1, kontrola jest przenoszona z powrotem do rozwiązania, a proces jest powtarzany dla Project2.

     Ten sam proces tworzenia projektów zagnieżdżonych odbywa się dla projektu podrzędnego, który ma element podrzędny. W takim przypadku, jeśli BuildProject1, który jest elementem podrzędnym Project1, miało projekty podrzędne, zostałyby utworzone po BuildProject1 i przed Project2. Proces jest cykliczny, a hierarchia jest tworzona od góry.

     Gdy projekt zagnieżdżony jest zamknięty, ponieważ użytkownik zamknął rozwiązanie lub konkretny projekt, wywoływana jest inna metoda w `IVsParentProject` , <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A> . Projekt nadrzędny otacza wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> metody z <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> metodami powiadamiania odbiorników z zdarzeniami rozwiązania, które są zamykane w zagnieżdżonych projektach.

W poniższych tematach opisano kilka innych koncepcji, które należy wziąć pod uwagę podczas implementowania zagnieżdżonych projektów:

- [Zagadnienia dotyczące zwalniania i ponownego ładowania zagnieżdżonych projektów](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Obsługa kreatora dla zagnieżdżonych projektów](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Implementowanie obsługi poleceń dla zagnieżdżonych projektów](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrowanie okna dialogowego AddItem dla zagnieżdżonych projektów](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Zobacz też

- [Dodaj elementy do okna dialogowego Dodaj nowy element](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Rejestruj szablony projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)
- [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parametry kontekstu](../../extensibility/internals/context-parameters.md)
- [Plik kreatora (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
