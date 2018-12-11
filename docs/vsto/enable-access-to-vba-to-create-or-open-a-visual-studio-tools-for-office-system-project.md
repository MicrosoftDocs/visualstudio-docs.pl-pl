---
title: Zapewnianie dostępu do VBA można utworzyć lub otworzyć Visual Studio Tools dla programu Microsoft Office project systemu
decsprition: You must explicitly enable access to the Office VBA project system before you can create or open a Visual Studio Tools for Office system project
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vst.project.vbawrongversion
- VST.Project.VBASecurityGenericError
- VST.Project.VBASecurityPermissions
- VST.SelectDocWizard.MissingCOM
- VST.Project.VBASecurityNotSet
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f17c4e1481e7f33034e16d1e60a285b25c6f8230
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34448994"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Zapewnianie dostępu do VBA można utworzyć lub otworzyć Visual Studio Tools dla programu Microsoft Office project systemu

Musisz jawnie włączyć dostęp do Visual Basic dla aplikacji (VBA) projektu systemu Microsoft Office przed można utworzyć lub otworzyć Visual Studio Tools dla programu Microsoft Office project systemu.

 Microsoft Office rozwoju projektów wymagają dostępu do języka Visual Basic dla aplikacji (VBA) system projektu w programie Microsoft Office Word i Microsoft Office Excel, nawet jeśli projekty nie należy używać języka Visual Basic for Applications. Obsługa projektowania formantów w projektach zarówno Visual Basic i C# zależy od języka Visual Basic for system projektu aplikacji.

 Niektóre wirusy makro Microsoft Office próba zautomatyzować Visual Basic for system projektu aplikacji w celu propagowania samodzielnie. Po włączeniu dostępu do programu Visual Basic dla aplikacji systemu projektu, należy usunąć zabezpieczenie, która pomaga zapobiegać rozpowszechniania wirusów. Jednak normalne makro zabezpieczeń jest uwzględniany, więc poziom zabezpieczeń makr i listę zaufanych wydawców, które utrzymują dla aplikacji pakietu Office określi, czy wszystkie makra jest uruchamiana na komputerze.

> [!NOTE]
> Dotyczy to tylko na komputerze deweloperskim. Komputerów użytkowników końcowych do uruchamiania rozwiązań pakietu Office po włączeniu tej opcji nie jest konieczne.

 Należy pamiętać, że wyłączanie dostępu do programu Visual Basic dla aplikacji systemu projektu na jego własnej nie chroni przed wirusami, ale po prostu można zatrzymać niektórych wirusy rozprzestrzeniania się na inne dokumenty, jeśli komputer staje się coraz zainfekowany za pomocą makra przed wirusami. Opcja jest domyślnie wyłączona jako dodatkową warstwę ochrony dla tego komputera, ale jej włączeniu nie powoduje komputera więcej podatny na wirusy Jeśli wykonujesz najlepszych rozwiązań dotyczących zabezpieczeń.

 Najlepsze ochrony przed wirusami jest do uruchomienia z pakietu Office na wysoki lub bardzo wysoki poziom zabezpieczeń, tylko zaufania makra z zweryfikowane, znane źródła pakietu Office i na bieżąco z programy antywirusowe i poprawek zabezpieczeń.

 Aby uzyskać więcej informacji dotyczących ochrony komputera przed wirusami i innych złośliwy kod, zobacz [ http://www.microsoft.com/protect ](http://www.microsoft.com/protect).

 Można włączyć lub wyłączyć opcję **zaufania dostępu do projektu Visual Basic** ręcznie.

 Zobacz VBA lub COM błędów można naprawić instalację pakietu Office.

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Aby włączyć lub wyłączyć dostęp do projektów Visual Basic

1. Kliknij przycisk **pliku** kartę.

2. Kliknij przycisk **opcje**.

3. Kliknij przycisk **Centrum zaufania**, a następnie kliknij przycisk **ustawienia Centrum zaufania**.

4. W **Centrum zaufania**, kliknij przycisk **ustawienia makr**.

5. Zaznaczenie lub usunięcie zaznaczenia **zaufania dostępu do modelu obiektowego projektu VBA** Aby włączyć lub wyłączyć dostęp do projektów Visual Basic.

6. Kliknij przycisk **OK**.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>Aby włączyć lub wyłączyć dostęp do projektów Visual Basic z pakietu Microsoft Office 2007

1. Na **narzędzia** menu w Word czy Excel wskaż **makro**, a następnie kliknij przycisk **zabezpieczeń**.

2. W **zabezpieczeń** okno dialogowe, kliknij przycisk **zaufanych wydawców** kartę.

3. Wybierz, aby włączyć lub usuń zaznaczenie, aby wyłączyć, **zaufania dostępu do projektu Visual Basic**.

4. Kliknij przycisk **OK**.

## <a name="to-set-your-office-macro-security-level"></a>Aby ustawić poziom zabezpieczeń makr pakietu Office

1. Kliknij przycisk **pliku** kartę.

2. Kliknij przycisk **opcje**.

3. Kliknij przycisk **Centrum zaufania**, a następnie kliknij przycisk **ustawienia Centrum zaufania**.

4. W **Centrum zaufania**, kliknij przycisk **ustawienia makr**.

5. W **ustawienia makr** wybierz odpowiednie ustawienie.

6. Kliknij przycisk **OK**.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>Aby ustawić poziom zabezpieczeń makr pakietu Office przy użyciu systemu Microsoft Office 2007

1. Na **narzędzia** menu w Word czy Excel wskaż **makro**, a następnie kliknij przycisk **zabezpieczeń**.

2. Na **poziom zabezpieczeń** , a następnie wybierz odpowiednie ustawienie.

    **Poziom zabezpieczeń** karta zawiera szczegółowe informacje o każdym poziomie. Aby uzyskać więcej informacji zobacz temat "Poziomów zabezpieczeń makr" w Pomocy.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>Aby zainstalować VBA przy użyciu systemu Microsoft Office 2007

1. W Panelu sterowania, uruchom **Dodaj lub usuń programy** lub **programy i funkcje**.

2. Wybierz urząd **aktualnie zainstalowane programy** listy.

3. Kliknij przycisk **zmiany**.

4. Wybierz **Dodaj lub usuń funkcje**, a następnie kliknij przycisk **Kontynuuj**.

5. Wybierz **Wybierz zaawansowane dostosowywanie aplikacji**, a następnie kliknij przycisk **dalej**.

6. Rozwiń węzeł **wspólne funkcje pakietu Office** w **wybierz opcje aktualizacji aplikacji i narzędzi** listy.

7. Otwórz menu rozwijanym obok pozycji **Visual Basic for Applications**, a następnie kliknij przycisk **uruchamianie z komputera**.

8. Kliknij przycisk **Kontynuuj**.

9. Kliknij przycisk **Zamknij**.

## <a name="to-repair-your-installation-of-office"></a>Aby naprawić instalację pakietu Office

1. W Panelu sterowania, uruchom **Dodaj lub usuń programy** lub **programy i funkcje**.

2. Wybierz używanej wersji pakietu Office w **aktualnie zainstalowane programy** listy.

3. Kliknij przycisk **zmiany**.

4. Wybierz **Zainstaluj ponownie lub napraw**, a następnie kliknij przycisk **dalej**.

5. Wybierz **Wykryj i napraw błędy instalacji pakietu Office**, a następnie kliknij przycisk **zainstalować**.

## <a name="see-also"></a>Zobacz także

 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)