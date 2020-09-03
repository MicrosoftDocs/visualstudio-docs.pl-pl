---
title: Projekty i rozwiązania, Opcje — okno dialogowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 245b453a3020e79b924cb8058ff392bd59673402
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662132"
---
# <a name="projects-and-solutions-options-dialog-box"></a>Opcje projektów i rozwiązań — okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ustawia domyślną ścieżkę [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] folderów projektu i określa domyślne zachowanie okna **danych wyjściowych** , **Lista zadań**i **Eksplorator rozwiązań** jako projekty są tworzone i kompilowane. Aby uzyskać dostęp do tego okna dialogowego, kliknij przycisk **Narzędzia/Opcje** rozwiń węzeł **projekty i rozwiązania**, a następnie kliknij pozycję **Ogólne**.

> [!NOTE]
> Opcje dostępne w oknach dialogowych oraz nazwy i lokalizacje poleceń menu, które są widoczne, mogą się różnić od tego, co opisano w pomocy, w zależności od ustawień aktywnych lub wydania. Ta strona pomocy została zaprojektowana z uwzględnieniem **ogólnych ustawień deweloperskich** . Aby wyświetlić lub zmienić ustawienia, wybierz pozycję **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="settings"></a>Ustawienia
 **Lokalizacja projektów** Ustawia domyślną lokalizację, w której są tworzone nowe projekty i foldery rozwiązań i katalogi. Kilka okien dialogowych używa również lokalizacji ustawionej w tej opcji dla punktów początkowych folderu. Na przykład okno dialogowe Otwieranie projektu używa tej lokalizacji dla skrótu moje projekty.

 **Lokalizacja szablonów projektu użytkownika** Ustawia domyślną lokalizację używaną przez okno dialogowe **Nowy projekt** , aby utworzyć listę **moich szablonów**. Aby uzyskać więcej informacji, zobacz [How to: Lokalizowanie i organizowanie szablonów](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

 **Lokalizacja szablonów elementów użytkownika** Ustawia domyślną lokalizację używaną przez okno dialogowe **Dodaj nowy element** , aby utworzyć listę **moich szablonów**. Aby uzyskać więcej informacji, zobacz [How to: Lokalizowanie i organizowanie szablonów](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

 **Zawsze pokazuj lista błędów, jeśli kompilacja zakończy się z błędami** Otwiera okno **Lista błędów** po zakończeniu kompilacji, tylko wtedy, gdy kompilacja projektu nie powiodła się. Zostaną wyświetlone błędy występujące podczas procesu kompilacji. Gdy ta opcja jest wyczyszczona, błędy nadal występują, ale okno nie jest otwierane po zakończeniu kompilacji. Ta opcja jest domyślnie włączona.

 **Śledź aktywny element w Eksplorator rozwiązań** Po wybraniu **Eksplorator rozwiązań** automatycznie otwierane, a aktywny element jest zaznaczony. Wybrany element zmienia się podczas pracy z różnymi plikami w projekcie lub rozwiązaniu lub różnymi składnikami projektanta. Gdy ta opcja jest wyczyszczona, wybór w **Eksplorator rozwiązań** nie zmienia się automatycznie. Ta opcja jest domyślnie włączona.

 **Pokaż zaawansowane konfiguracje kompilacji** Po wybraniu opcji konfiguracji kompilacji są wyświetlane w oknie dialogowym **strony właściwości projektu** i w oknie dialogowym **strony właściwości rozwiązania** . Po wyczyszczeniu opcji konfiguracji kompilacji nie są wyświetlane w oknie dialogowym **strony właściwości projektu** i w oknie dialogowym **strony właściwości rozwiązania** dla [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projektów, które zawierają jedną konfigurację lub dwie konfiguracje debugowanie i wydanie. Jeśli projekt zawiera konfigurację zdefiniowaną przez użytkownika, są wyświetlane opcje konfiguracji kompilacji.

 W przypadku usunięcia zaznaczenia polecenia w menu **kompilacja** , takie jak **rozwiązanie do kompilowania**, ponowne **Kompilowanie rozwiązania**i **czyste rozwiązanie**, są wykonywane w konfiguracji wydania i polecenia w menu **Debuguj** , takie jak **Rozpocznij debugowanie** i **Uruchom bez debugowania**, są wykonywane w konfiguracji debugowania.

 **Zawsze pokazuj rozwiązanie** Po wybraniu rozwiązanie i wszystkie polecenia działające na rozwiązaniach są zawsze wyświetlane w środowisku IDE. Po wyczyszczeniu wszystkie projekty są tworzone jako projekty autonomiczne, a rozwiązanie nie jest widoczne w Eksplorator rozwiązań lub polecenia, które działają na rozwiązaniach w IDE, jeśli rozwiązanie zawiera tylko jeden projekt.

 **Zapisuj nowe projekty po utworzeniu** Po wybraniu można określić lokalizację projektu w oknie dialogowym **Nowy projekt** . Po wyczyszczeniu wszystkie nowe projekty są tworzone jako projekty tymczasowe. Podczas pracy z projektami tymczasowymi można tworzyć i eksperymentować z projektem bez konieczności określania lokalizacji na dysku.

 **Ostrzegaj użytkownika, gdy Lokalizacja projektu nie jest zaufana** Jeśli spróbujesz utworzyć nowy projekt lub otworzyć istniejący projekt w lokalizacji, która nie jest w pełni zaufana (na przykład w ścieżce UNC lub w ścieżce HTTP), zostanie wyświetlony komunikat. Użyj tej opcji, aby określić, czy komunikat jest wyświetlany za każdym razem, gdy próbujesz utworzyć lub otworzyć projekt w lokalizacji, która nie jest w pełni zaufana.

 **Pokaż okno danych wyjściowych po rozpoczęciu kompilacji** Automatycznie wyświetla Okno Dane wyjściowe w środowisku IDE na początku kompilacji rozwiązania. Aby uzyskać więcej informacji, zobacz [How to: Control the okno dane wyjściowe](https://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858). Ta opcja jest domyślnie włączona.

 **Monituj o zmianę nazwy symbolicznej podczas zmiany nazwy plików** Po wybraniu Wyświetla okno komunikatu z pytaniem, czy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] należy również zmienić nazwy wszystkich odwołań w projekcie na element kodu.

## <a name="see-also"></a>Zobacz też
 [Okno dialogowe Opcje, Projekty i rozwiązania, Kompilowanie i uruchamianie](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
