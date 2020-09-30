---
title: Dostęp VBA do tworzenia/otwierania projektu systemu narzędzi VSTO
titleSuffix: ''
decsprition: You must explicitly enable access to the Office VBA project system before you can create or open a Visual Studio Tools for Office system project
ms.custom: seodec18
ms.date: 08/14/2019
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 71e30a89bdf8547eab9ed9c51b07c49e014b7302
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584862"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Włącz dostęp do języka VBA, aby utworzyć lub otworzyć Visual Studio Tools dla projektu systemu Microsoft Office

Aby można było utworzyć lub otworzyć Visual Studio Tools dla projektu systemu Microsoft Office, należy jawnie włączyć dostęp do systemu projektu Visual Basic for Applications (VBA) w programie Microsoft Office.

 Projekty deweloperskie Microsoft Office wymagają dostępu do systemu projektu Visual Basic for Applications (VBA) w Microsoft Office Word i Microsoft Office Excel, nawet jeśli projekty nie używają Visual Basic for Applications. Obsługa kontrolek w czasie projektowania w projektach Visual Basic i C# zależy od systemu Visual Basic for Applications Project.

 Niektóre Microsoft Office wirusy makr podejmują próbę zautomatyzowania systemu Visual Basic for Applications projektu jako środek do propagowania siebie. Przez umożliwienie dostępu do systemu projektu Visual Basic for Applications, należy usunąć ochronę, która pomaga zapobiegać rozproszeniu wirusów makr. Jednak normalne zabezpieczenia makr pozostają na miejscu, dlatego poziom zabezpieczeń makr i lista zaufanych wydawców obsługiwanych przez aplikacje pakietu Office określają, czy dowolne makro jest uruchamiane na komputerze.

> [!NOTE]
> Dotyczy to tylko komputera deweloperskiego. Na komputerach użytkowników końcowych nie jest wymagana opcja uruchamiania rozwiązań pakietu Office.

 Należy pamiętać, że wyłączenie dostępu do samodzielnego systemu projektowego Visual Basic for Applications nie chroni przed wirusami, a po prostu pomaga zapobiec rozproszeniu niektórych wirusów do innych dokumentów, jeśli komputer zostanie zainfekowany wirusem makra. Opcja jest domyślnie wyłączona jako dodaną warstwę ochrony dla komputera, ale włączenie jej nie sprawia, że komputer jest bardziej podatny na wirusy, jeśli są stosowane najlepsze rozwiązania w zakresie zabezpieczeń.

 Najlepszą ochroną przed wirusami makr pakietu Office jest uruchamianie pakietu Office na wysokim lub bardzo wysokim poziomie zabezpieczeń, a jedynie ufają makrom ze zweryfikowanych, znanych źródeł i na bieżąco z poprawkami zabezpieczeń i skanerami wirusów.

 Można włączać lub wyłączać opcję **Ufaj dostępowi do Visual Basic Project** ręcznie.

 Instalację pakietu Office można naprawić, jeśli wystąpią błędy VBA lub COM.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Aby włączyć lub wyłączyć dostęp do projektów Visual Basic

1. Kliknij kartę **plik** .

2. Kliknij pozycję **Opcje**.

3. Kliknij pozycję **Centrum zaufania**, a następnie kliknij pozycję **Ustawienia Centrum zaufania**.

4. W **Centrum zaufania**kliknij pozycję **Ustawienia makr**.

5. Zaznacz lub usuń zaznaczenie **zaufania dostępu do modelu obiektów projektu VBA,** aby włączyć lub wyłączyć dostęp do projektów Visual Basic.

6. Kliknij przycisk **OK**.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>Aby włączyć lub wyłączyć dostęp do projektów Visual Basic przy użyciu systemu Microsoft Office 2007

1. W menu **Narzędzia** w programie Word lub Excel wskaż polecenie **makro**, a następnie kliknij pozycję **zabezpieczenia**.

2. W oknie dialogowym **zabezpieczenia** kliknij kartę **Zaufani wydawcy** .

3. Wybierz, aby włączyć, lub wyczyść, aby wyłączyć, **ufać dostępowi do Visual Basic projektu**.

4. Kliknij przycisk **OK**.

## <a name="to-set-your-office-macro-security-level"></a>Aby ustawić poziom zabezpieczeń makr pakietu Office

1. Kliknij kartę **plik** .

2. Kliknij pozycję **Opcje**.

3. Kliknij pozycję **Centrum zaufania**, a następnie kliknij pozycję **Ustawienia Centrum zaufania**.

4. W **Centrum zaufania**kliknij pozycję **Ustawienia makr**.

5. W sekcji **Ustawienia makr** wybierz odpowiednie ustawienie.

6. Kliknij przycisk **OK**.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>Aby ustawić poziom zabezpieczeń makr pakietu Office przy użyciu systemu Microsoft Office 2007

1. W menu **Narzędzia** w programie Word lub Excel wskaż polecenie **makro**, a następnie kliknij pozycję **zabezpieczenia**.

2. Na karcie **poziom zabezpieczeń** wybierz odpowiednie ustawienie.

    Karta **poziom zabezpieczeń** zawiera szczegółowe informacje o każdym poziomie. Aby uzyskać więcej informacji, zobacz temat "poziomy zabezpieczeń makr" w pomocy pakietu Office.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>Aby zainstalować język VBA w systemie 2007 Microsoft Office

1. W panelu sterowania uruchom **aplet Dodaj lub usuń programy** lub **programy i funkcje**.

2. Wybierz pozycję Office na liście **Aktualnie zainstalowane programy** .

3. Kliknij przycisk **Zmień**.

4. Wybierz pozycję **Dodaj lub usuń funkcje**, a następnie kliknij przycisk **Kontynuuj**.

5. Wybierz pozycję **Wybierz zaawansowane dostosowywanie aplikacji**, a następnie kliknij przycisk **dalej**.

6. Rozwiń pozycję **funkcje udostępnione pakietu Office** na liście **Wybierz Opcje aktualizacji dla aplikacji i narzędzi** .

7. Otwórz menu rozwijane obok **Visual Basic for Applications**, a następnie kliknij pozycję **Uruchom z mojego komputera**.

8. Kliknij pozycję **Kontynuuj**.

9. Kliknij przycisk **Zamknij**.

## <a name="to-repair-your-installation-of-office"></a>Aby naprawić instalację pakietu Office

1. W panelu sterowania uruchom **aplet Dodaj lub usuń programy** lub **programy i funkcje**.

2. Wybierz wersję pakietu Office z listy **aktualnie zainstalowanych programów** .

3. Kliknij przycisk **Zmień**.

4. Wybierz pozycję **Zainstaluj ponownie lub napraw**, a następnie kliknij przycisk **dalej**.

5. Wybierz pozycję **Wykryj i napraw błędy w instalacji pakietu Office**, a następnie kliknij przycisk **Instaluj**.

## <a name="see-also"></a>Zobacz też
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
