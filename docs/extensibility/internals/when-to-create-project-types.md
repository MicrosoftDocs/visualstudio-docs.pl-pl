---
title: Kiedy tworzyć typy projektów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 861250dac25288f353cbd5c57f510bf67dadce70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703430"
---
# <a name="when-to-create-project-types"></a>Kiedy należy tworzyć typy projektów
Tworzenie nowego typu projektu stanowi podstawę do dostosowania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dla użytkowników. Jednak tworzenie nowego typu projektu nie jest wymagane dla wszystkich [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostosowań. Poniższe wskazówki powinny pomóc w ustaleniu, czy dla danego scenariusza jest wymagany nowy typ projektu.

## <a name="create-a-new-project-type"></a>Utwórz nowy typ projektu
 Należy utworzyć typ projektu, jeśli chcesz dostosować [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] się do działania na co najmniej jeden z następujących sposobów:

- Uczestnictwo w kompilacjach, wdrażaniu, konfiguracjach i kontroli źródła.

- Oferowanie pomocy technicznej dotyczącej debugowania.

- Wyświetl elementy projektu w **Eksplorator rozwiązań**.

- Użyj okna dialogowego **Otwórz projekt** lub **Nowy projekt** .

- Obsługa zagnieżdżania projektów.

## <a name="extend-an-existing-project-type"></a>Rozwiń istniejący typ projektu
 Można utworzyć nowy typ projektu, który może być używany [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w następujących sposobach, aby zmodyfikować lub zwiększyć zachowanie istniejącego typu projektu, na przykład modyfikując proces kompilacji dla [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektów:

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
 Można użyć podtypów projektu, aby rozłożyć typ projektu zarządzanego bez konieczności tworzenia nowego typu projektu. Podtypy projektu używają agregacji COM do rozbudowania zarządzanych projektów utworzonych w firmie Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] . Dzięki agregacji COM można ponownie wykorzystać większość zarządzanych implementacji systemu projektu i nadal dostosowywać się do określonego scenariusza za pomocą agregacji i używania interfejsów pomocniczych. Aby uzyskać więcej informacji na temat podtypów projektów, zobacz [podtypy projektów](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Zobacz też
- [Okna dokumentów i edytory](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
