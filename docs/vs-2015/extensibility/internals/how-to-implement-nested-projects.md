---
title: 'Porady: Implementowanie zagnieżdżonych projektów | Dokumentacja firmy Microsoft'
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
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8a392b8b336c57c47055357147075f29ba173d8f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810133"
---
# <a name="how-to-implement-nested-projects"></a>Porady: Implementowanie zagnieżdżonych projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podczas tworzenia projektu zagnieżdżonego typu są kilka dodatkowych kroków, które muszą zostać zaimplementowane. Projekt nadrzędny przejmuje niektóre z tych samych obowiązków, które rozwiązanie ma jego projektów zagnieżdżonych (elementów podrzędnych). Projekt nadrzędny jest kontenerem projektów, które są podobne do rozwiązania. W szczególności istnieje kilka zdarzeń, które muszą zostać wywołane przez rozwiązania i projekty nadrzędnego do tworzenia hierarchii zagnieżdżonych projektów. Zdarzenia te są opisane w ramach następującego procesu tworzenia zagnieżdżonych projektów.  
  
### <a name="to-create-nested-projects"></a>Aby utworzyć zagnieżdżonych projektów  
  
1. Zintegrowanego środowiska programistycznego (IDE) ładuje informacje plików i uruchamiania projektów projektu nadrzędnego, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfejsu. Projekt nadrzędny zostanie utworzony i dodany do rozwiązania.  
  
   > [!NOTE]
   >  W tym momencie jest zbyt wczesny procesu dla projektu nadrzędnego do utworzenia projektu zagnieżdżonego, ponieważ projekt nadrzędny musi zostać utworzony przed utworzeniem projektów podrzędnych. Po tej sekwencji projekt nadrzędny można stosować ustawienia dla projektów podrzędnych, i projektów podrzędnych można pobrać informacji z projektów nadrzędnego, w razie potrzeby. Ta sekwencja jest, jeśli jest ona potrzebna w przez klientów, takich jak kontroli kodu źródłowego (SCC) i Eksplorator rozwiązań.  
  
    Projekt nadrzędny musi czekać <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> metoda wywoływana przez środowisko IDE, zanim można utworzyć jego zagnieżdżonych (podrzędny) w projekcie lub w projektach.  
  
2. Wywołania środowiska IDE `QueryInterface` projekt nadrzędny dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>. Jeśli to wywołanie zakończy się powodzeniem, wywołania IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> metoda elementu nadrzędnego, aby otworzyć wszystkie zagnieżdżonych projektów dla projektu nadrzędnego.  
  
3. Wywoływanych w projekcie nadrzędnego <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> metoda o zagnieżdżonych projektów mają zostać utworzone. SCC, na przykład nasłuchuje tych zdarzeń, aby dowiedzieć się, jeśli czynności w procesie tworzenia rozwiązania i projektu są wykonywane w kolejności. Jeśli kroki pojawiają się poza kolejnością, rozwiązanie może nie być kontroli kodu źródłowego poprawnie zarejestrowany.  
  
4. Wywoływanych w projekcie nadrzędnego <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> metody lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> metody na każdym z jego projektów podrzędnych.  
  
    Możesz przekazać <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> do `AddVirtualProject` metodę w celu wskazania, czy wirtualny projekt (zagnieżdżona) powinien zostać dodany do okno projektu wyłączone z kompilacji, dodać do kontroli kodu źródłowego i tak dalej. `VSADDVPFLAGS` Umożliwia kontrolowanie widoczności elementu projektu zagnieżdżonego i wskazują, jakie funkcje są skojarzone z nim.  
  
    Jeśli załadujesz uprzednio istniejącego projektu podrzędnego, który ma projektu przechowywany w pliku projektu projektu nadrzędnego, wywoływanych w projekcie nadrzędny identyfikator GUID `AddVirtualProjectEx`. Jedyną różnicą między `AddVirtualProject` i `AddVirtualProjectEX` jest fakt, że `AddVirtualProjectEX` ma parametr, aby włączyć projekt nadrzędny określić dla każdego wystąpienia `guidProjectID` dla projektu podrzędnego, aby włączyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> funkcji poprawnie.  
  
    Jeżeli nie jest dostępny, żaden identyfikator GUID, takie jak podczas dodawania nowego projektu zagnieżdżonego rozwiązanie spowoduje utworzenie go dla projektu w czasie, który zostanie dodany do elementu nadrzędnego. Jest odpowiedzialny za projekt nadrzędny można utrwalić projektu identyfikator GUID w pliku projektu. Jeśli usuniesz projektu zagnieżdżonego, identyfikator GUID dla tego projektu mogą być również usuwane.  
  
5. Wywołania środowiska IDE `M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren` metody dla każdego projektu podrzędnego projektu nadrzędnego.  
  
    Projekt nadrzędny musi implementować element `IVsParentProject` Aby zagnieździć projektów. Ale nadrzędnego projektu nigdy nie wywołuje `QueryInterface` dla `IVsParentProject` nawet wtedy, gdy ma ona projektów nadrzędne, podrzędne. Rozwiązanie obsługuje wywołanie `IVsParentProject` i, jeśli jest stosowana, wywołuje metodę `OpenChildren` do tworzenia projektów zagnieżdżonych. `AddVirtualProjectEX` zawsze jest wywoływany z `OpenChildren`. Nigdy nie powinna być wywoływana przez projekt nadrzędnej, aby zachować hierarchię tworzenia zdarzeń w kolejności.  
  
6. Wywołania środowiska IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> metody na projekt podrzędny.  
  
7. Wywoływanych w projekcie nadrzędnego <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> metoda o utworzeniu projektów podrzędnych dla obiektu nadrzędnego.  
  
8. Wywołania środowiska IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> metody w projekcie nadrzędnym, po otwarciu wszystkich projektów podrzędnych.  
  
    Jeśli go jeszcze nie istnieje, projekt nadrzędny tworzy identyfikator GUID dla każdego projektu zagnieżdżonego, wywołując `CoCreateGuid`.  
  
   > [!NOTE]
   >  `CoCreateGuid` Interfejs API modelu COM jest wywoływana, gdy ma zostać utworzony identyfikator GUID. Aby uzyskać więcej informacji, zobacz `CoCreateGuid` i identyfikatory GUID w bibliotece MSDN.  
  
    Ten identyfikator GUID są zapisane w projekcie nadrzędnej w pliku projektu mają być pobrane przy następnym, który jest otwierany w środowisku IDE. Zobacz krok 4, aby uzyskać więcej informacji dotyczących wywołania `AddVirtualProjectEX` można pobrać `guidProjectID` dla projektu podrzędnego.  
  
9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Następnie wywoływana jest metoda identyfikator elementu nadrzędnego zgodnie z Konwencją delegowanie w do projektu zagnieżdżonego. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Pobiera właściwości węzła, który zagnieżdżony projekt, który ma działać delegowanie w wywołanego w nadrzędnej.  
  
     Ponieważ nadrzędne i podrzędne projekty są tworzone programowo, można ustawić właściwości dla zagnieżdżonych projektów w tym momencie.  
  
    > [!NOTE]
    >  Nie tylko, czy są wyświetlane informacje o kontekście z projektu zagnieżdżonego, ale można również zadawać, jeśli projekt nadrzędny ma dowolnego kontekstu dla tego elementu, sprawdzając <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>. W ten sposób możesz dodać dodatkowe atrybuty dynamiczna Pomoc i opcje menu określonych dla poszczególnych projektów zagnieżdżonych.  
  
10. Hierarchia zaprojektowano pod kątem wyświetlania w oknie Eksploratora rozwiązań z wywołaniem <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> metody.  
  
     Przekazać hierarchii do środowiska za pomocą `GetNestedHierarchy` do tworzenia hierarchii do wyświetlenia w oknie Eksploratora rozwiązań. W ten sposób rozwiązania wie, że projekt istnieje i mogą być zarządzane do tworzenia przez Menedżera kompilacji lub można zezwolić na pliki w projekcie, które należy umieścić pod kontrolą kodu źródłowego.  
  
11. Po utworzeniu wszystkich zagnieżdżonych projektów dla projektu Project1 sterowanie jest przekazywane do rozwiązania, a proces jest powtarzany podczas o nazwie Project2.  
  
     Występuje ten sam proces tworzenia zagnieżdżonych projektów dla projektu podrzędnego, który ma element podrzędny. W tym przypadku BuildProject1, który jest elementem podrzędnym projektu Project1, gdyby projekty podrzędne zostaną utworzone po BuildProject1 i przed o nazwie Project2. Ten proces jest cykliczna, a hierarchia została stworzona od góry w dół.  
  
     Po zamknięciu projektu zagnieżdżonego, ponieważ użytkownik zamknął rozwiązania lub określonego projektu, inna metoda na `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, jest wywoływana. Projekt nadrzędny opakowuje wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> metody z <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> metody o rozwiązaniu zdarzenia są zamykane zagnieżdżonych projektów.  
  
    Poniższe tematy dotyczy kilka innych koncepcji, które należy wziąć pod uwagę podczas implementowania zagnieżdżonych projektów:  
  
    [Zagadnienia dotyczące zwalniania i ponownego ładowania zagnieżdżonych projektów](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
    [Obsługa kreatora dla zagnieżdżonych projektów](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
    [Implementowanie obsługi poleceń dla zagnieżdżonych projektów](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
    [Filtrowanie okna dialogowego Dodawanie elementu dla projektów zagnieżdżonych](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie elementów do Dodaj nowy element okien dialogowych](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parametry kontekstu](../../extensibility/internals/context-parameters.md)   
 [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

