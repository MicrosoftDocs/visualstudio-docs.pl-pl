---
title: Dostosowywanie modelu z profilami i stereotypami | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, profiles
- UML model, stereotypes
- UML model, customizing
ms.assetid: fd607157-0d3a-4583-a84e-427a4b2a5acb
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f7e9aee38208a96ab75318a86810359392b5b8e1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433354"
---
# <a name="customize-your-model-with-profiles-and-stereotypes"></a>Dostosowywanie modelu za pomocą profilów i stereotypów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można dostosować standardowe elementy modelu UML, takie jak klas i składników, aby dostosować je do określonych celów. Można zastosować *stereotyp* do elementu modelu, który można zmienić elementu listy właściwości. Stereotypy są zdefiniowane w kolekcji o nazwie *profile*.  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Aby użyć stereotypu, możesz połączyć pakiet do profilu. Dzięki temu można również zastosować Stereotypy, które są zdefiniowane w profilu do elementów w pakiecie. Niektóre profile są instalowane razem z Visual Studio. Ponadto można zdefiniować własne profile.  
  
 Na liście właściwości elementu można ustawić stereotypów. Dla głównych typów kształt na diagramie Stereotypy zastosowane również zostać wyświetlony w kształcie, jak pokazano w przykładzie.  
  
 ![Klasa UML, stereotypu. ](../modeling/media/uml-class-stereotype.png "UML_class_stereotype")  
  
> [!NOTE]
> Jeśli używasz profilu do tworzenia modelu, a następnie udostępnisz model innym osobom, będą mogli zobaczyć stereotypów, chyba że zainstalowali ten sam profil na swoich komputerach.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Dodawanie stereotypów do elementów modelu UML](../modeling/add-stereotypes-to-uml-model-elements.md)|Wprowadzenie do elementu modelu w pakiecie, łączenie pakiet z profilu i stosowanie stereotyp do elementu.|  
|[Standardowe stereotypy dla modeli UML](../modeling/standard-stereotypes-for-uml-models.md)|Standardowa L2 profilów UML i L3 są instalowane z programem Visual Studio, a każdy model jest połączony z nich domyślnie. Zapewniają one stereotypów, których można dodawać adnotacje do Twoich modeli.<br /><br /> Na przykład stereotyp «specyfikacji» można zastosować do klasy, aby wskazać, czy jest przeznaczona wyłącznie w celu zdefiniowania-widocznych zewnętrznych zachowań jego wystąpień|  
|[Definiowanie profilu w celu rozszerzenia kodu UML](../modeling/define-a-profile-to-extend-uml.md)|Można zdefiniować własne stereotypów i narzędzia, które są dostosowane do własnego obszaru aplikacji.<br /><br /> Na przykład jeśli opracowania oprogramowania bankowego, można zdefiniować stereotyp «Konto», który można zastosować do klasy. Można następnie użyć diagramów klas do opisania różnych typów kont i ich wzajemne relacje.|  
|[Instalowanie profilu UML](../modeling/install-a-uml-profile.md)|Jeśli ktoś ma profil UML, można zainstalować go na komputerze.|  
|[Definiowanie niestandardowego elementu przybornika modelowania](../modeling/define-a-custom-modeling-toolbox-item.md)|Element przybornika niestandardowego zapisuje z wielokrotnie ustawienie stereotyp na nowe elementy.|  
|[Kolor klas UML przez stereotyp](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|Ten przykładowy kod rozszerza diagramów UML. Automatycznie ustawia jego kolor kształtu UML, zgodnie z stereotyp elementu.|
