---
title: 'Instrukcje: Wyświetlanie istniejących typów (Projektant klas) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 45a4dd40e00182084686841279f81eb1de9d8a28
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63424580"
---
# <a name="how-to-view-existing-types-class-designer"></a>Instrukcje: Wyświetlanie istniejących typów (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby wyświetlić istniejący typ i jej elementów członkowskich, należy dodać jego kształtu do diagramu klas.  
  
 Można zobaczyć typy lokalne i typy odwołania. Typ lokalny istnieje w aktualnie otwartym projekcie i jest do odczytu/zapisu. Typ odwołania istnieje w innym projekcie lub w zestawie odwołania i jest tylko do odczytu.  
  
 Aby zaprojektować nowe typy diagramów klas, zobacz [jak: Tworzenie typów za pomocą projektanta klas](../ide/how-to-create-types-by-using-class-designer.md).  
  
### <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Aby wyświetlić typy w projekcie na diagramie klasy  
  
1. Z projektu w Eksploratorze rozwiązań otwórz istniejący plik diagramu klasy (.cd). Lub jeśli nie istnieje żaden diagram klas, dodaj nowy diagram klas do projektu. Zobacz [jak: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).  
  
2. Z projektu w oknie Eksploratora rozwiązań przeciągnij plik z kodem źródłowym do diagramu klasy.  
  
   > [!WARNING]
   > Jeśli rozwiązanie ma projektu, który udostępnia kod przez wiele aplikacji, można przeciągnąć pliki lub kod do diagramu klasy tylko z tych źródeł:  
   > 
   > - Projekt aplikacji, który zawiera diagram  
   >   - Współdzielony projekt zaimportowany przez projekt aplikacji  
   >   - Projekt odwołania  
   >   - Zestaw  
  
    Kształty przedstawiające typy zdefiniowane w pliku kodu źródłowego są wyświetlane na diagramie w miejscu, gdzie przeciągnąłeś plik.  
  
   Typy można także wyświetlić w projekcie, przeciągając jeden lub więcej typów z węzła projektu w Widoku klas do diagramu klasy.  
  
> [!TIP]
> Jeśli widok klas nie jest otwarty, otwórz widok klas z **widoku** menu. Aby uzyskać więcej informacji dotyczących widoku klas, zobacz [Viewing Classes and Their Members](http://msdn.microsoft.com/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).  
  
 Aby wyświetlić typy w lokalizacjach domyślnych na diagramie, zaznacz jeden lub więcej typów w widoku klas kliknij prawym przyciskiem myszy wybrane typy i wybierz **Pokaż Diagram klas**.  
  
> [!NOTE]
> Jeśli zamknięty diagram klas zawierający typ już istnieje w projekcie, diagram klas się otworzy, aby wyświetlić kształt typu. Jednakże, jeśli w projekcie nie istnieje diagram klas zawierający typ, Projektant klasy tworzy nowy diagram klas w projekcie i otwiera go, aby wyświetlić typ.  
  
 Przy pierwszym wyświetleniu typu na diagramie, jego kształt pojawia się domyślnie zwinięty. Można rozwinąć kształt, aby wyświetlić jego zawartość.  
  
### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Aby wyświetlić zawartość projektu na diagramie klasy  
  
1. W Eksploratorze rozwiązań lub w widoku klas kliknij prawym przyciskiem myszy projekt i wybierz polecenie **widoku**, następnie wybierz **Pokaż Diagram klas**.  
  
     Tworzony jest automatycznie wypełniony Diagram klas.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Wyświetlanie dziedziczenia między typami (Projektant klas)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Instrukcje: Dostosowywanie diagramów klas (Projektant klas)](../ide/how-to-customize-class-diagrams-class-designer.md)   
 [Wyświetlanie typów i relacji (Projektant klas)](../ide/viewing-types-and-relationships-class-designer.md)
