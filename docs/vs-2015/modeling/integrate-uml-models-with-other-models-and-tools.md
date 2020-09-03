---
title: Integruj modele UML z innymi modelami i narzędziami | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, references to models
ms.assetid: 9e75e7d1-93cf-4196-baa3-bd10b9af16d3
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72ea0c562bb9c2a8050fc1365fac19df20232f80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918356"
---
# <a name="integrate-uml-models-with-other-models-and-tools"></a>Integrowanie modeli UML z innymi modelami i narzędziami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modele UML można zintegrować z innymi modelami i z językami specyficznymi dla domeny.

 Można zintegrować modele na następujące sposoby, pisząc kod rozszerzenia w celu wykonywania różnych funkcji:

 Dołącz odwołania z dowolnego elementu do innych elementów, takich jak pliki lub elementy w innych modelach.
W elemencie UML można przechowywać linki do innych elementów UML, plików lub innych obiektów przez kodowanie ich tożsamości jako ciągi.

 Można na przykład napisać rozszerzenie, które może połączyć dowolną akcję UML (czyli element na diagramie aktywności) z innym diagramem aktywności. Gdy użytkownik kliknie dwukrotnie akcję, zostanie otwarty inny diagram. Pozwala to użytkownikowi na dostarczenie bardziej szczegółowego widoku akcji.

 Istnieją dwa sposoby przechowywania ciągów i innych danych w dowolnym elemencie:

- **Właściwości stereotypu.** Można zdefiniować profil UML, w którym definiuje się stereotyp, który dodaje właściwości do określonych rodzajów elementu UML. Na przykład można zdefiniować profil, który dodaje właściwość o nazwie **MoreDetail** do akcji UML. Można napisać kod rozszerzenia, który przechowuje dane łączy w akcji przez zastosowanie stereotypu do akcji, a następnie przechowywanie danych we właściwości.

   Stereotyp i jego właściwości są widoczne dla użytkownika w okno Właściwości.

   Aby wdrożyć to rozszerzenie, należy spakować definicję profilu i kod rozszerzenia w jednym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzeniu.

   Aby uzyskać więcej informacji, zobacz [Definiowanie profilu do rozszerania UML](../modeling/define-a-profile-to-extend-uml.md).

- **Wołują.** Możesz dołączyć zestaw ciągów do dowolnego elementu UML. Można napisać kod przechowujący informacje, takie jak nazwa pliku lub identyfikator GUID innego elementu. Można to zrobić bez podawania dodatkowych definicji. Odwołania nie są bezpośrednio widoczne dla użytkownika.

Istnieją dwa sposoby kodowania odwołań do elementów modelu:

- **Identyfikator GUID i nazwa pliku** docelowego elementu modelu oraz model, który go zawiera, lub określony diagram, który go wyświetla.

- **Odwołania ModelBus.** ModelBus to struktura służąca do tworzenia i rozwiązywania odwołań między modelami. Zawiera selektor ModelBus, który umożliwia użytkownikowi wybranie elementu w modelu. Pomaga również użytkownikowi w rozwiązywaniu odwołań, które zostały utracone ze względu na zmiany w modelu docelowym.

   Aby uzyskać więcej informacji, zobacz [integrowanie modeli za pomocą programu Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

  Propaguj zmiany z jednego modelu do innego.
  Można na przykład zsynchronizować nazwę elementu z nazwą połączonego diagramu, tak aby w przypadku zmiany jednego użytkownika zmiany były również zmieniane. W tym celu należy wykonać dwa mechanizmy:

1. **Reguły VMSDK** mogą służyć do propagowania zmian w tym samym modelu.

2. **Zdarzenia VMSDK** mogą służyć do propagowania zmian poza modelem — na przykład w celu zmiany nazwy pliku połączonego dokumentu lub zmiany elementu w innym modelu.

   Aby uzyskać informacje o obu tych mechanizmach, zobacz [How to: reagować na zmiany w modelu UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).

   Przeciągnij elementy, aby skopiować je z jednego modelu do drugiego, można pozwolić użytkownikom na tworzenie elementów przez przeciąganie elementów na diagram UML. Utworzony element nie musi być kopią oryginału. Na przykład możesz pozwolić, aby użytkownik przeciągnieł diagram aktywności z Eksploratora rozwiązań na inny diagram aktywności, aby utworzyć nową akcję.

   Aby uzyskać więcej informacji, zobacz [Definiowanie obsługi gestów na diagramie modelowania](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) i [instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="see-also"></a>Zobacz też
 [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Definiowanie procedury obsługi gestów na diagramie modelowania](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) [instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md) [jak: reagowanie na zmiany w modelu UML](../misc/how-to-respond-to-changes-in-a-uml-model.md)
