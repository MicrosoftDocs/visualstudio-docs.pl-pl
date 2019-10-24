---
title: Kiedy tworzyć typy projektów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff29843965c220c505266a9cd973e5695c0b9dab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721554"
---
# <a name="when-to-create-project-types"></a>Kiedy należy tworzyć typy projektów
Tworzenie nowego typu projektu stanowi podstawę do dostosowywania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dla użytkowników. Jednak tworzenie nowego typu projektu nie jest wymagane dla wszystkich dostosowań [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Poniższe wskazówki powinny pomóc w ustaleniu, czy dla danego scenariusza jest wymagany nowy typ projektu.

## <a name="create-a-new-project-type"></a>Utwórz nowy typ projektu
 Należy utworzyć typ projektu, jeśli chcesz dostosować [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do działania na co najmniej jeden z następujących sposobów:

- Uczestnictwo w kompilacjach, wdrażaniu, konfiguracjach i kontroli źródła.

- Oferowanie pomocy technicznej dotyczącej debugowania.

- Wyświetl elementy projektu w **Eksplorator rozwiązań**.

- Użyj okna dialogowego **Otwórz projekt** lub **Nowy projekt** .

- Obsługa zagnieżdżania projektów.

## <a name="extend-an-existing-project-type"></a>Rozwiń istniejący typ projektu
 Możesz chcieć utworzyć nowy typ projektu, który może używać [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w następujący sposób, aby zmodyfikować lub zwiększyć zachowanie istniejącego typu projektu, na przykład modyfikując proces kompilacji dla projektów [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]:

- Pracuj z wieloma plikami jako pojedynczą jednostką.

- Wyświetla jeden plik jako hierarchię elementów podrzędnych.

- Wyświetlanie kontekstu poleceń wokół edytorów.

- Wyświetlanie kontekstu usługi dla edytorów.

## <a name="use-an-existing-project-type"></a>Użyj istniejącego typu projektu
 Tworzenie nowego projektu nie jest czasami konieczne. W poniższej tabeli przedstawiono zadania, które nie są potrzebne do utworzenia typu projektu dla.

|Zadanie|Opis|
|----------|-----------------|
|Obsługa poleceń|Każdy pakietu VSPackage może obsłużyć polecenia.|
|Kompilowanie edytora|Edytory niestandardowe mogą być rejestrowane. Aby uzyskać więcej informacji, zobacz [dokumentowanie okien i edytorów](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc).|
|Okna posiadające własność|Można utworzyć okna narzędzi i dokumentów bez dodawania nowego typu projektu.|
|Uwidacznianie właściwości w okno Właściwości|Wszystkie obiekty mogą uwidaczniać właściwości.|

## <a name="create-a-project-subtype"></a>Utwórz podtyp projektu
 Można użyć podtypów projektu, aby rozłożyć typ projektu zarządzanego bez konieczności tworzenia nowego typu projektu. Podtypy projektu używają agregacji COM do rozbudowania zarządzanych projektów utworzonych w programie Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Dzięki agregacji COM można ponownie wykorzystać większość zarządzanych implementacji systemu projektu i nadal dostosowywać się do określonego scenariusza za pomocą agregacji i używania interfejsów pomocniczych. Aby uzyskać więcej informacji na temat podtypów projektów, zobacz [podtypy projektów](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Zobacz także
- [Okna dokumentów i edytory](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)