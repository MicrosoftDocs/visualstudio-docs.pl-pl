---
title: Kiedy utworzyć typy projektów | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703430"
---
# <a name="when-to-create-project-types"></a>Kiedy należy tworzyć typy projektów
Tworzenie nowego typu projektu stanowi podstawę [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do dostosowywania dla użytkowników. Jednak tworzenie nowego typu projektu nie jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wymagane dla wszystkich dostosowań. Poniższe wskazówki powinny pomóc w określeniu, czy nowy typ projektu jest wymagany dla twojego scenariusza.

## <a name="create-a-new-project-type"></a>Tworzenie nowego typu projektu
 Należy utworzyć typ projektu, jeśli chcesz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostosować do działania w jeden lub więcej z następujących sposobów:

- Weź udział w tworzeniu, wdrażaniu, konfiguracjach i kontroli źródła.

- Zaoferuj obsługę debugowania.

- Wyświetlanie elementów projektu w **Eksploratorze rozwiązań**.

- Okno dialogowe **Otwórz projekt** lub **Nowy projekt.**

- Obsługa zagnieżdżania projektów.

## <a name="extend-an-existing-project-type"></a>Rozszerzanie istniejącego typu projektu
 Można utworzyć nowy typ projektu, który [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] można użyć w następujący sposób, aby zmodyfikować lub rozszerzyć zachowanie istniejącego [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] typu projektu, na przykład modyfikując proces kompilacji dla projektów:

- Praca z wieloma plikami jako pojedyncza jednostka.

- Wyświetlanie pojedynczego pliku jako hierarchii podelementów.

- Wyświetlanie kontekstu polecenia wokół edytorów.

- Wyświetlanie kontekstu usługi dla edytorów.

## <a name="use-an-existing-project-type"></a>Używanie istniejącego typu projektu
 Tworzenie nowego projektu czasami nie jest konieczne. W poniższej tabeli przedstawiono zadania, dla których nie trzeba tworzyć typu projektu.

|Zadanie|Opis|
|----------|-----------------|
|Obsługa poleceń|Każdy vspackage może obsługiwać polecenia.|
|Tworzenie edytora|Edytory niestandardowe mogą być rejestrowane. Aby uzyskać więcej informacji, zobacz [System Windows i Edytory dokumentów](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc).|
|Posiadanie okien|Okna narzędzi i dokumentów można tworzyć bez dodawania nowego typu projektu.|
|Udostępnianie właściwości w oknie Właściwości|Wszystkie obiekty mogą ujawniać właściwości.|

## <a name="create-a-project-subtype"></a>Tworzenie podtypu projektu
 Podtypów projektu można użyć do rozszerzenia typu zarządzanego projektu bez konieczności tworzenia nowego typu projektu. Podtypy projektu używają agregacji COM do [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] rozszerzania zarządzanych projektów napisanych w firmie Microsoft lub [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Za pomocą agregacji COM można ponownie użyć dużej części implementacji systemu projektu zarządzanego i nadal dostosowywać dla określonego scenariusza za pomocą agregacji i korzystania z interfejsów pomocniczych. Aby uzyskać więcej informacji na temat podtypów projektu, zobacz [Podtypy projektu](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Zobacz też
- [Dokument systemu Windows i edytorów](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
