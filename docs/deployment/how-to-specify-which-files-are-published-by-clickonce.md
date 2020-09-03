---
title: Jak określić, które pliki są publikowane przez ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, file exclusion
- files, publishing via ClickOnce
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7ab6d724b40168f84227edb6ccfafc6245c30e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85381785"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Instrukcje: Określanie, które pliki są publikowane przez ClickOnce
Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji wszystkie pliki niebędące kodem w projekcie są wdrażane wraz z aplikacją. W niektórych przypadkach może nie być konieczne lub nie trzeba publikować niektórych plików lub instalować niektórych plików na podstawie warunków. Program Visual Studio udostępnia funkcje do wykluczania plików, oznaczania plików jako plików danych lub wymagań wstępnych oraz tworzenia grup plików na potrzeby instalacji warunkowej.

 Pliki [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji są zarządzane w oknie dialogowym **pliki aplikacji** dostępne na stronie **Publikuj** w **projektancie projektu**.

 Początkowo istnieje Pojedyncza grupa plików o nazwie **(wymagana)**. Można tworzyć dodatkowe grupy plików i przypisywać do nich pliki. Nie można zmienić **grupy pobierania** dla plików, które są wymagane do uruchomienia aplikacji. Na przykład aplikacja. exe lub pliki oznaczone jako pliki danych muszą należeć do grupy **(wymagane)** .

 Domyślna wartość stanu publikowania pliku jest oznaczona za pomocą **(Auto)**. Na przykład aplikacja. exe ma domyślnie stan publikacji **include (Auto)** .

 Pliki z właściwością **Akcja kompilacji** ustawioną na **zawartość** są wyznaczane jako pliki aplikacji i będą domyślnie oznaczone jako uwzględnione. Mogą być dołączane, wykluczone lub oznaczane jako pliki danych. Wyjątki są następujące:

- Pliki danych, takie jak pliki SQL Database (*. mdf* i *. mdb*) i pliki XML, zostaną domyślnie oznaczone jako pliki danych.

- Odwołania do zestawów (pliki *. dll* ) są wystawiane w następujący sposób podczas dodawania odwołania: Jeśli **copy Local** ma **wartość false**, jest domyślnie oznaczony jako zestaw wymagań wstępnych (**Autoinstalacja**), który musi być obecny w pamięci GAC przed zainstalowaniem aplikacji. Jeśli **kopia lokalna** ma **wartość true**, zestaw jest oznaczony domyślnie jako zestaw aplikacji (**include (Auto)**) i zostanie skopiowany do folderu aplikacji podczas instalacji. Odwołanie COM zostanie wyświetlone w oknie dialogowym **pliki aplikacji** (jako plik *ocx* ) tylko wtedy, gdy jego właściwość **izolowana** ma **wartość true**. Domyślnie zostanie on uwzględniony.

### <a name="to-add-files-to-the-application-files-dialog-box"></a>Aby dodać pliki do okna dialogowego pliki aplikacji

1. Wybierz plik danych w **Eksplorator rozwiązań**.

2. W okno Właściwości zmień właściwość **Akcja kompilacji** na wartość **zawartość** .

### <a name="to-exclude-files-from-clickonce-publishing"></a>Aby wykluczyć pliki z publikacji ClickOnce

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. Kliknij przycisk **pliki aplikacji** , aby otworzyć okno dialogowe **pliki aplikacji** .

4. W oknie dialogowym **pliki aplikacji** wybierz plik, który ma zostać wykluczony.

5. W polu **Publikuj stan** wybierz opcję **Wyklucz** z listy rozwijanej.

### <a name="to-mark-files-as-data-files"></a>Aby oznaczyć pliki jako pliki danych

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. Kliknij przycisk **pliki aplikacji** , aby otworzyć okno dialogowe **pliki aplikacji** .

4. W oknie dialogowym **pliki aplikacji** wybierz plik, który chcesz oznaczyć jako dane.

5. W polu **Publikuj stan** wybierz z listy rozwijanej pozycję **plik danych** .

### <a name="to-mark-files-as-prerequisites"></a>Aby oznaczyć pliki jako wstępnie wymagane

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. Kliknij przycisk **pliki aplikacji** , aby otworzyć okno dialogowe **pliki aplikacji** .

4. W oknie dialogowym **pliki aplikacji** wybierz zestaw aplikacji (plik *. dll* ), który ma zostać oznaczony jako warunek wstępny. Zwróć uwagę, że aplikacja musi mieć odwołanie do zestawu aplikacji, aby było ono widoczne na liście.

5. W polu **Publikuj stan** wybierz pozycję **wymaganie wstępne** z listy rozwijanej.

### <a name="to-add-a-new-file-group"></a>Aby dodać nową grupę plików

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. Kliknij przycisk **pliki aplikacji** , aby otworzyć okno dialogowe **pliki aplikacji** .

4. W oknie dialogowym **pliki aplikacji** wybierz pole **grupy** dla pliku, który chcesz dołączyć do nowej grupy.

    > [!NOTE]
    > Aby nazwy plików pojawiły się w oknie dialogowym **pliki aplikacji** , dla plików musi być ustawiona właściwość **Akcja kompilacji** na wartość **zawartość** .

5. W polu **Grupa pobierania** wybierz pozycję **\<New...>** z listy rozwijanej.

6. W oknie dialogowym **Nowa grupa** wprowadź nazwę grupy, a następnie kliknij przycisk **OK**.

### <a name="to-add-a-file-to-a-group"></a>Aby dodać plik do grupy

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. Kliknij przycisk **pliki aplikacji** , aby otworzyć okno dialogowe **pliki aplikacji** .

4. W oknie dialogowym **pliki aplikacji** wybierz pole **grupy** dla pliku, który chcesz dołączyć do nowej grupy.

5. W polu **Grupa pobierania** wybierz grupę z listy rozwijanej.

    > [!NOTE]
    > Nie można zmienić **grupy pobierania** dla plików, które są wymagane do uruchomienia aplikacji.

## <a name="see-also"></a>Zobacz też
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)