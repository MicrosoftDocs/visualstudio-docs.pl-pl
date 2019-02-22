---
title: Kiedy należy tworzyć typy projektów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 45bd40d2261a30ea455132ba92841c33b968eac0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614990"
---
# <a name="when-to-create-project-types"></a>Kiedy należy tworzyć typy projektów
Tworzenie nowych typów projektów stanowi podstawę do dostosowywania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dla użytkowników. Jednak tworzenie nowy typ projektu nie jest wymagane w przypadku wszystkich [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostosowań. Poniższe wskazówki pomoże określić, czy nowy typ projektu jest wymagana dla danego scenariusza.

## <a name="create-a-new-project-type"></a>Utwórz nowy typ projektu
 Należy utworzyć typ projektu, jeśli chcesz dostosować [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do działania w co najmniej jednej z następujących sposobów:

-   Uczestniczy w kompilacji, wdrażania, konfiguracji i kontroli źródła.

-   Oferuje obsługę debugowania.

-   Wyświetl elementy projektu w **Eksploratora rozwiązań**.

-   Użyj **Otwórz projekt** lub **nowy projekt** okno dialogowe.

-   Zagnieżdżanie projektów pomocy technicznej.

## <a name="extend-an-existing-project-type"></a>Rozszerzyć istniejący typ projektu
 Należy utworzyć nowy typ projektu, można użyć [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pod następującymi względami do modyfikowania lub rozszerzania działania istniejącego typu projektu, na przykład, modyfikując procesem kompilacji dla [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektów:

-   Praca z wieloma plikami jako pojedyncza jednostka.

-   Wyświetl pojedynczy plik jako hierarchię elementów podrzędnych.

-   Wyświetlanie w kontekście polecenia wokół edytorów.

-   Wyświetl kontekstu usługi dla edytorów.

## <a name="use-an-existing-project-type"></a>Użyj istniejącego typu projektu
 Tworzenie nowego projektu Czasami nie jest konieczne. W poniższej tabeli przedstawiono zadania, które jest konieczne tworzenie typu projektu.

|Zadanie|Opis|
|----------|-----------------|
|Obsługa poleceń|Dowolnego pakietu VSPackage może obsługiwać poleceń.|
|Tworzenie edytora|Można zarejestrować edytorach niestandardowych. Aby uzyskać więcej informacji, zobacz [Windows dokumentu i edytory](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc).|
|Będącej właścicielem systemu windows|Bez dodawania nowych typów projektów, można utworzyć okna dokumentów i narzędzi.|
|Uwidacznianie właściwości w oknie dialogowym właściwości|Wszystkie obiekty można ujawnić właściwości.|

## <a name="create-a-project-subtype"></a>Utwórz podtypu projektu
 Podtypy projektów można użyć w celu rozszerzania typu zarządzanego projektu bez konieczności tworzenia nowego typu projektu. Podtypy projektów użycia agregacji COM, aby rozszerzyć projektów zarządzanych, napisane w firmie Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Za pomocą agregacji COM można ponownie użyć większość implementacji systemu zarządzanego projektu i nadal dostosować do danego scenariusza za pomocą agregacji i umożliwia korzystanie z obsługi interfejsów. Aby uzyskać więcej informacji na temat podtypy projektów, zobacz [podtypy projektów](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Zobacz też
- [Windows dokumentu i edytory](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)