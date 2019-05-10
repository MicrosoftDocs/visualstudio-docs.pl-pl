---
title: Jak zarządzać konfiguracje usług i profilów | Dokumentacja firmy Microsoft
description: Dowiedz się, jak pracować z plikami konfiguracji usługi konfiguracji i profile | które przechowywania ustawień dla środowisk wdrażania i ustawienia publikowania dla usługi w chmurze.
author: ghogen
manager: jillfra
assetId: 7da8c551-fb06-4057-b5c7-c77f4b39d803
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/11/2017
ms.author: ghogen
ms.openlocfilehash: 353b98ae0ab186a4ff665566a8f3b7600db66274
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62569034"
---
# <a name="how-to-manage-service-configurations-and-profiles"></a>Jak zarządzać profilami i konfiguracjami usług
## <a name="overview"></a>Omówienie
Podczas publikowania usługi w chmurze programu Visual Studio przechowuje informacje o konfiguracji w dwa rodzaje plików konfiguracyjnych: usługi konfiguracji i profilów. Konfiguracja usługi (.cscfg pliki) przechowywania ustawień dla środowiska wdrażania usługi w chmurze platformy Azure. Platforma Azure używa tych plików konfiguracji, gdy zarządza usługi w chmurze. Z drugiej strony profile (pliki .azurePubxml) magazynu ustawień publikowania dla usługi w chmurze. Te ustawienia są rekordu wybierz możesz za pomocą Kreatora publikacji, gdy są używane lokalnie przez program Visual Studio. W tym temacie wyjaśniono, jak działają z oboma typami plików konfiguracyjnych.

## <a name="service-configurations"></a>Konfiguracja usługi
Możesz utworzyć wiele konfiguracji usługi do użytku dla każdego środowiska wdrażania. Na przykład może utworzyć z konfiguracją usługi dla środowiska lokalnego, która umożliwia uruchamianie i testowanie aplikacji systemu Azure a inną konfigurację usługi w środowisku produkcyjnym.

Możesz dodać, usunąć, zmienić nazwę i modyfikować te konfiguracje usługi, w zależności od wymagań. Te konfiguracje usługi można zarządzać z poziomu programu Visual Studio, jak pokazano na poniższej ilustracji.

![Zarządzanie konfiguracjami usługi](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-service-config.png)

Możesz również otworzyć **Zarządzanie konfiguracjami** okno dialogowe ze stron właściwości roli. Aby otworzyć właściwości dla roli w projekcie platformy Azure, otwórz menu skrótów dla tej roli, a następnie wybierz **właściwości**. Na **ustawienia** kartę, a następnie rozwiń **konfiguracji usługi** listy, a następnie wybierz **Zarządzaj** otworzyć **Zarządzanie konfiguracjami** okno dialogowe.

### <a name="to-add-a-service-configuration"></a>Aby dodać konfigurację usługi
1. W Eksploratorze rozwiązań Otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz pozycję **Zarządzanie konfiguracjami**.

    **Konfiguracje usługi Zarządzanie** pojawi się okno dialogowe.
2. Aby dodać konfigurację usługi, należy utworzyć kopię istniejącej konfiguracji. Aby to zrobić, wybierz konfigurację, którą chcesz skopiować z listy nazw, a następnie wybierz pozycję **Utwórz kopię**.
3. (Opcjonalnie) Aby konfiguracja usługi inną nazwę, wybierz nową konfigurację usługi z listy nazw, a następnie wybierz **Zmień nazwę**. W **nazwa** tekstu wpisz nazwę, która ma być używana dla tej konfiguracji usługi, a następnie wybierz pozycję **OK**.

    Nowy plik konfiguracji usługi o nazwie ServiceConfiguration. [Nazwa nowego] .cscfg jest dodawany do projektu platformy Azure w Eksploratorze rozwiązań.

### <a name="to-delete-a-service-configuration"></a>Aby usunąć konfigurację usługi
1. W Eksploratorze rozwiązań Otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz pozycję **Zarządzanie konfiguracjami**.

    **Konfiguracje usługi Zarządzanie** pojawi się okno dialogowe.
2. Aby usunąć konfigurację usługi, wybierz konfigurację, którą chcesz usunąć z **nazwa** listy, a następnie wybierz pozycję **Usuń**. Aby sprawdzić, czy chcesz usunąć tę konfigurację, pojawi się okno dialogowe.
3. Wybierz pozycję **Usuń**.

     Plik konfiguracji usługi zostanie usunięty z projektu platformy Azure w Eksploratorze rozwiązań.

### <a name="to-rename-a-service-configuration"></a>Aby zmienić konfigurację usługi
1. W Eksploratorze rozwiązań Otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz **Zarządzanie konfiguracjami**.

    **Konfiguracje usługi Zarządzanie** pojawi się okno dialogowe.
2. Aby zmienić nazwę konfiguracji usługi, wybierz nową konfigurację usługi z **nazwa** listy, a następnie wybierz **Zmień nazwę**. W **nazwa** tekstu wpisz nazwę, która ma być używana dla tej konfiguracji usługi, a następnie wybierz **OK**.

    Nazwa pliku konfiguracji usługi jest zmieniona w projekcie platformy Azure w Eksploratorze rozwiązań.

### <a name="to-change-a-service-configuration"></a>Aby zmienić konfigurację usługi
* Jeśli chcesz zmienić konfiguracji usługi, otwórz menu skrótów dla określonej roli, aby zmiany w projekcie platformy Azure, a następnie wybierz **właściwości**. Zobacz [jak: Konfigurowanie ról dla usługi Azure Cloud Service za pomocą programu Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md) Aby uzyskać więcej informacji.

## <a name="make-different-setting-combinations-by-using-profiles"></a>Wprowadź ustawienie różnych kombinacji przy użyciu profilów
Za pomocą profilu, można automatycznie wypełnić **Kreatora publikacji** z różnymi kombinacjami ustawienia do różnych celów. Na przykład może mieć jeden profil debugowania, a drugi dla wersji kompilacji. W takim przypadku swoje **debugowania** miałby profilu **IntelliTrace** włączone i **debugowania** wybranej, konfiguracji i **wersji** Profil musi **IntelliTrace** wyłączone i **wersji** wybranej konfiguracji. Aby wdrożyć usługę przy użyciu innego konta magazynu można także użyć różnych profilów.

Po uruchomieniu kreatora po raz pierwszy, tworzony jest profil domyślny. Programu Visual Studio są przechowywane w pliku, który posiada rozszerzenie .azurePubXml, który zostanie dodany do projektu platformy Azure w ramach profilu **profile** folderu. Jeśli po uruchomieniu kreatora później ręcznie określić różne opcje, plik jest automatycznie aktualizacji. Przed rozpoczęciem poniższej procedury, powinien już opublikowany usługi w chmurze co najmniej raz.

### <a name="to-add-a-profile"></a>Aby dodać profil
1. Otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz **Publikuj**.
2. Obok pozycji **docelowy profil** listy wybierz **Zapisz profil** przycisku, jak pokazano na następującym rysunku. Spowoduje to utworzenie profilu dla Ciebie.

    ![Utwórz nowy profil](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/create-new-profile.png)
3. Po utworzeniu profilu wybierz **< Zarządzaj >** w **docelowy profil** listy.

    **Spravovat profily** pojawi się okno dialogowe, jak pokazano na następującym rysunku.

    ![Zarządzanie profilami okna dialogowego](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-profiles.png)
4. W **nazwa** listy, wybierz profil, a następnie wybierz **Utwórz kopię**.
5. Wybierz **Zamknij** przycisku.

    Nowy profil zostanie wyświetlony na liście profilów docelowej.
6. W **docelowy profil** , wybierz profil, który został utworzony na liście. Ustawienia kreatora Publikowanie są wypełniane wybór z wybranego profilu.
7. Wybierz **Wstecz** i **dalej** przycisków, aby wyświetlić każdą stronę w Kreatorze publikacji, a następnie dostosować ustawienia dla tego profilu. Zobacz [Kreator publikowania aplikacji Azure](http://go.microsoft.com/fwlink/p/?LinkID=623085) informacji.
8. Po zakończeniu dostosowywania ustawień wybierz **dalej** aby wrócić do strony ustawień. Profil zostanie zapisany podczas publikowania usługi za pomocą tych ustawień lub jeśli zostanie wybrana **Zapisz** obok listy profilów.

### <a name="to-rename-or-delete-a-profile"></a>Aby zmienić lub usunąć profil
1. Otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz **Publikuj**.
2. W **docelowy profil** listy wybierz **Zarządzaj**.
3. W **spravovat profily** okno dialogowe, wybierz profil, który chcesz usunąć, a następnie wybierz pozycję **Usuń**.
4. W oknie dialogowym potwierdzenia wybierz **OK**.
5. Wybierz **Zamknij**.

### <a name="to-change-a-profile"></a>Aby zmienić profil
1. Otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz **Publikuj**.
2. W **docelowy profil** listy, wybierz profil, który chcesz zmienić.
3. Wybierz **Wstecz** i **dalej** przycisków, aby wyświetlić każdą stronę w Kreatorze publikacji, a następnie zmień odpowiednie ustawienia. Zobacz [Kreator publikowania aplikacji Azure](http://go.microsoft.com/fwlink/p/?LinkID=623085) informacji.
4. Po zakończeniu wprowadzania zmian, zmiany ustawień, wybierz **dalej** aby wrócić do **ustawienia** strony.
5. (Opcjonalnie) wybierz **Publikuj** opublikować usługę w chmurze przy użyciu nowych ustawień. Jeśli nie chcesz opublikować usługi w chmurze, w tym momencie, a następnie zamknij Kreatora publikacji, Visual Studio monituje o tym, jeśli chcesz zapisać zmiany wprowadzone do profilu.

## <a name="next-steps"></a>Następne kroki
Aby dowiedzieć się więcej o konfigurowaniu innych części projektu platformy Azure z programu Visual Studio, zobacz [Konfigurowanie projektu platformy Azure](http://go.microsoft.com/fwlink/p/?LinkID=623075)
