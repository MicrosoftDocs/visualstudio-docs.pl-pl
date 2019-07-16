---
title: Integrowanie modeli UML z innymi modelami i narzędziami | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, references to models
ms.assetid: 9e75e7d1-93cf-4196-baa3-bd10b9af16d3
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1a8b67e5c784e24b1af71089d33e7db60cb1f92c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68190386"
---
# <a name="integrate-uml-models-with-other-models-and-tools"></a>Integrowanie modeli UML z innymi modelami i narzędziami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modele UML można zintegrować z innymi modelami i języki specyficzne dla domeny.  
  
 Pisząc kod rozszerzenia do wykonywania różnych funkcji, można zintegrować modele w następujący sposób:  
  
 Należy dołączyć odwołania z dowolnego elementu do innych elementów, takich jak pliki lub do elementów w innych modeli.  
 W elemencie UML można przechowywać łącza do innych elementów UML, plików lub innych obiektów przez kodowanie ich tożsamości jako ciągi.  
  
 Na przykład można napisać rozszerzenia, które można połączyć dowolną akcję UML (czyli element na diagramie aktywności) do innego diagramu aktywności. Gdy użytkownik kliknie dwukrotnie akcji, zostanie otwarty inny diagram. Dzięki temu użytkownikowi podanie bardziej szczegółowy widok akcji.  
  
 Istnieją dwa sposoby, w których można przechowywać ciągi i inne dane w dowolny element:  
  
- **Właściwości stereotypu.** Można zdefiniować profil UML, w której definiujesz stereotypu, który dodaje właściwości do określonego rodzaju elementu UML. Na przykład można zdefiniować profil, który dodaje właściwość o nazwie **MoreDetail** akcji UML. Można napisać kod rozszerzenia połączenia przez magazyny danych w celu wykonania akcji przez zastosowanie stereotyp do akcji, a następnie zapisując dane we właściwości.  
  
   Stereotyp i jego właściwości są widoczne dla użytkownika w oknie dialogowym właściwości.  
  
   Aby wdrożyć to rozszerzenie, czy pakiet definicji profilu i kod rozszerzenia w ramach pojedynczej [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia.  
  
   Aby uzyskać więcej informacji, zobacz [Definiowanie profilu w celu rozszerzenia UML](../modeling/define-a-profile-to-extend-uml.md).  
  
   Aby uzyskać przykładowy projekt, w której profil, który jest wdrażany wraz z poleceń menu i program obsługi gestów, zobacz [próbki: Profilów UML](http://go.microsoft.com/fwlink/?LinkID=213811).  
  
- **Odwołania.** Zestaw ciągów można dołączyć do dowolnego elementu UML. Można napisać kod, który przechowuje informacje, takie jak nazwa pliku lub identyfikator GUID innego elementu. Można to zrobić bez podawania dodatkowe definicje. Odwołania nie są bezpośrednio widoczne dla użytkownika.  
  
   Aby uzyskać więcej informacji, zobacz [elementów modelu dołączanie ciągów odwołania do UML](../modeling/attach-reference-strings-to-uml-model-elements.md). Dla przykładu, zobacz [łącze elementów UML, diagramy lub innych plików](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
  Istnieją dwa sposoby, aby zakodować odwołania do elementów modelu:  
  
- **Identyfikator GUID i nazwę pliku** elementu modelu docelowego i model, który zawiera go lub określonego diagram, który wyświetla je.  
  
   Aby uzyskać przykład, zobacz [łącze elementów UML, diagramy lub innych plików](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
- **Odwołania ModelBus.** ModelBus to architektura służąca do tworzenia i rozpoznawanie odwołań między modelami. Obejmuje ona selektorze ModelBus informuje użytkownika, wybierz pozycję elementu w modelu. Pomaga również użytkownika w celu rozwiązania odwołań, które zostaną utracone z powodu zmian w modelu docelowym.  
  
   Aby uzyskać więcej informacji, zobacz [integrowanie modeli za pomocą programu Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
  Propagowanie zmian z jednego modelu.  
  Na przykład można zsynchronizować nazwa elementu o nazwie połączone diagramu, więc, że jeśli użytkownik zmieni się jeden, druga zmienia także. Istnieją dwa mechanizmy w ten sposób:  
  
1. **Reguły VMSDK** może służyć do propagujące zmiany wewnątrz tego samego modelu.  
  
    Aby uzyskać przykład, zobacz [łącze elementów UML, diagramy lub innych plików](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
2. **Zdarzenia VMSDK** może służyć propagujące zmiany poza modelem — na przykład, Zmień nazwę pliku połączonego dokumentu lub zmienić elementu w innym modelem.  
  
   Aby uzyskać informacje o obu tych mechanizmów, zobacz [jak: Odpowiadanie na zmiany w modelu UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).  
  
   Przeciągnij elementy, aby je skopiować z jednego modelu do innego  
   Można pozwolić użytkownikom na tworzenie elementów, przeciągając elementy na UML diagram. Utworzony element ma być kopię oryginału. Na przykład można pozwolić użytkownika przeciągnij diagram aktywności z Eksploratora rozwiązań na inny diagram aktywności, aby utworzyć nową akcję.  
  
   Aby uzyskać więcej informacji, zobacz [definiowanie procedury obsługi gestów na diagramie modelowania](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) i [jak: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
## <a name="samples"></a>Przykłady  
 Zobacz przykładowy kod [łącze elementów UML, diagramy lub innych plików](http://go.microsoft.com/fwlink/?LinkId=213813). Przykład umożliwia użytkownikom, przeciągnij plik do dowolnego elementu UML, a później otworzyć go, klikając dwukrotnie plik elementu. Na przykład można połączyć diagram aktywności elementowi przypadków użycia. Ikona pojawi się elementy, które mają łącza.  
  
 Ten przykładowy kod przedstawia następujących technik:  
  
- [Dołączanie ciągów odwołania do elementów modelu UML](../modeling/attach-reference-strings-to-uml-model-elements.md)  
  
   Przykładowy kod ścieżki do plików i elementu identyfikatory GUID są przechowywane w ciągów odwołania, które są skojarzone z elementem.  
  
- Jak dodać dekoratorów do elementów UML. Aby uzyskać ogólne informacje na temat dekoratory zobacz [Dostosowywanie tekst i pola obrazu](../modeling/customizing-text-and-image-fields.md).  
  
   Przykładowa aplikacja dodaje dekoratora obrazu do kształtów UML.  
  
- [Instrukcje: Odpowiadanie na zmiany w modelu UML](../misc/how-to-respond-to-changes-in-a-uml-model.md)  
  
   W przykładzie pokazano, jak zdefiniować regułę, która odpowiada na nowe kształty znajdujące się na diagramie.  
  
- [Definiowanie polecenia menu w diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)  
  
- [Definiowanie procedury obsługi gestów na diagramie modelowania](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)  
  
   W przykładzie pokazano sposób obsługi elementów przeciągnięty z Eksploratora Windows (lub Eksploratora plików), Eksplorator rozwiązań i innych elementów UML.  
  
  Dla języka DSL odczytać przykładowi, w którym jest modelu UML, zobacz [jak: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definiowanie procedury obsługi gestów na diagramie modelowania](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)   
 [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Instrukcje: Odpowiadanie na zmiany w modelu UML](../misc/how-to-respond-to-changes-in-a-uml-model.md)   
 [Przykład: Profilów UML](http://go.microsoft.com/fwlink/?LinkID=213811)   
 [Link elementów UML, diagramy lub innych plików](http://go.microsoft.com/fwlink/?LinkId=213813)
