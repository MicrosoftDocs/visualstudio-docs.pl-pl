---
title: Tworzenie szablonów projektów i elementów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], projects
- item templates, about item templates
- templates [Visual Studio], item
- Visual Studio templates, item
- Visual Studio templates, about templates
- project templates [Visual Studio], about project templates
- Visual Studio templates, project
- templates [Visual Studio], about templates
ms.assetid: a6ce501a-699b-4e3e-ade8-c81895645c20
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 995696dafce64cdcb1fbb11d0788bbe13453c440
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619299"
---
# <a name="creating-project-and-item-templates"></a>Tworzenie szablonów projektów i elementów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablony projektu i elementu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zapewniają fragmenty do ponownego użycia udostępniające użytkownikom podstawowy kod i struktury, które można wykorzystać do własnych celów.

## <a name="visual-studio-templates"></a>Szablony Visual Studio
 Wiele wstępnie zdefiniowanych szablonów projektu i elementu jest instalowane podczas instalacji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Przykłady szablonów projektów [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] i [!INCLUDE[csprcs](../includes/csprcs-md.md)] Windows Forms aplikacji i biblioteki klas, które są dostępne w oknie dialogowym **Nowy projekt** . Szablony zainstalowanych elementów są dostępne w oknie dialogowym **Dodaj nowy element** , a także zawierają elementy, takie jak pliki kodu, pliki XML, strony HTML i arkusze stylów.

 Te szablony zapewniają punkt wyjścia dla użytkowników rozpoczynających tworzenie projektów lub rozszerzanie bieżących projektów. Szablony projektów dostarczają pliki, które są wymagane dla określonego typu projektu, zawierają odwołania do standardowego zestawu i ustawiają domyślne opcje kompilatora i właściwości projektu. Złożoność szablonów elementów może mieścić od zaledwie jednego pustego pliku, który ma poprawne rozszerzenie nazwy pliku po element wieloplikowy, który zawiera na przykład, pliki kodu źródłowego z kodem skróconym, informacje o projektancie plików i zasoby osadzone.

 Oprócz zainstalowanych szablonów w oknach dialogowych **Nowy projekt** i **Dodaj nowy element** można tworzyć własne szablony lub pobierać i używać szablonów utworzonych przez społeczność. Aby uzyskać więcej informacji, zobacz [How to: Create Project Templates](../ide/how-to-create-project-templates.md) and [How to: Create Item templates](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Zawartość szablonu
 Wszystkie szablony projektów i elementów, instalowane wraz z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub utworzone przez użytkownika, działają na podstawie tych samych zasad i spisu treści. Wszystkie szablony zawierają następujące elementy:

- Pliki, które można utworzyć, jeśli jest używany szablon. Dotyczy to plików kodu źródłowego, zasobów osadzonych, plików projektu i tak dalej.

- Jeden plik .vstemplate. Ten plik zawiera metadane, które dostarczają [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] informacji potrzebnych do wyświetlania szablonu w oknach dialogowych **Nowy projekt** i **Dodaj nowy element** oraz tworzenia projektu lub elementu z szablonu. Aby uzyskać więcej informacji na temat plików. vstemplate, zobacz [Parametry szablonu](../ide/template-parameters.md).

  Gdy te pliki są kompresowane do pliku zip i umieszczane w prawidłowym folderze, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] są automatycznie wyświetlane. Szablony projektu są wyświetlane w sekcji **Moje szablony** okien dialogowych **Nowy projekt** , a szablony elementów pojawiają się w oknach dialogowych **Dodawanie nowego elementu** . Aby uzyskać więcej informacji na temat folderów szablonów, zobacz [How to: Lokalizowanie i organizowanie szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="starter-kits"></a>Zestawy początkowe
 Zestawy startowe są rozszerzone przez szablony, które mogą być współużytkowane z innymi członkami społeczności. Zestaw startowy zawiera przykłady kodu, które kompilują, dokumentację i inne zasoby, aby pomóc użytkownikom poznać nowe narzędzia i techniki programowania, podczas tworzenia użytecznych, rzeczywistych aplikacji. Podstawowe zawartości i procedury zestawu startowego są identyczne z tymi szablonami. Aby uzyskać więcej informacji, zobacz [How to: Create Starter Kit](../ide/how-to-create-starter-kits.md).

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Tworzenie szablonów projektu](../ide/how-to-create-project-templates.md) [instrukcje: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md) [Parametry szablonu](../ide/template-parameters.md) [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md) [instrukcje: Tworzenie zestawów początkowych](../ide/how-to-create-starter-kits.md)
