---
title: Jak zarządzać konfiguracjami i profilami usług | Microsoft Docs
description: Dowiedz się, jak korzystać z konfiguracji usługi i plików konfiguracji profilów | Ustawienia przechowywania dla środowisk wdrażania i publikowania ustawień usług Cloud Services.
author: ghogen
manager: jillfra
assetId: 7da8c551-fb06-4057-b5c7-c77f4b39d803
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/11/2017
ms.author: ghogen
ms.openlocfilehash: b91e2df31ae0e188d0d1e0e3076ab410bf8c2296
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919834"
---
# <a name="how-to-manage-service-configurations-and-profiles"></a>Jak zarządzać profilami i konfiguracjami usług
## <a name="overview"></a>Omówienie
Po opublikowaniu usługi w chmurze program Visual Studio przechowuje informacje o konfiguracji w dwóch rodzajach plików konfiguracji: konfiguracje i profile usługi. Konfiguracje usług (pliki. cscfg) przechowują ustawienia dla środowisk wdrażania dla usługi w chmurze platformy Azure. Platforma Azure używa tych plików konfiguracji, gdy zarządza usługami w chmurze. Z drugiej strony profile (pliki azurePubxml) przechowują ustawienia publikowania usług Cloud Services. Te ustawienia są rekordem wybranych opcji podczas korzystania z Kreatora publikacji i są używane lokalnie przez program Visual Studio. W tym temacie wyjaśniono, jak korzystać z obu typów plików konfiguracji.

## <a name="service-configurations"></a>Konfiguracje usług
Można utworzyć wiele konfiguracji usługi, które będą używane dla każdego środowiska wdrażania. Można na przykład utworzyć konfigurację usługi dla środowiska lokalnego, która jest używana do uruchamiania i testowania aplikacji platformy Azure oraz innej konfiguracji usługi dla środowiska produkcyjnego.

Możesz dodawać, usuwać, zmieniać nazwy i modyfikować te konfiguracje usług zgodnie z wymaganiami. Tymi konfiguracjami usług można zarządzać z programu Visual Studio, jak pokazano na poniższej ilustracji.

![Zarządzanie konfiguracjami usług](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-service-config.png)

Możesz również otworzyć okno dialogowe **Zarządzanie konfiguracjami** ze stron właściwości roli. Aby otworzyć właściwości roli w projekcie platformy Azure, otwórz menu skrótów dla tej roli, a następnie wybierz polecenie **Właściwości**. Na karcie **Ustawienia** rozwiń listę **Konfiguracja usługi** , a następnie wybierz pozycję **Zarządzaj** , aby otworzyć okno dialogowe **Zarządzanie konfiguracjami** .

### <a name="to-add-a-service-configuration"></a>Aby dodać konfigurację usługi
1. W Eksplorator rozwiązań otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz pozycję **Zarządzaj konfiguracjami**.

    Zostanie wyświetlone okno dialogowe **Zarządzanie konfiguracjami usług** .
2. Aby dodać konfigurację usługi, należy utworzyć kopię istniejącej konfiguracji. W tym celu wybierz konfigurację, która ma zostać skopiowana z listy Nazwa, a następnie wybierz pozycję **Utwórz kopię**.
3. Obowiązkowe Aby nadać konfiguracji usługi inną nazwę, wybierz z listy Nazwa nową konfigurację usługi, a następnie wybierz pozycję **Zmień nazwę**. W polu tekstowym **Nazwa** wpisz nazwę, która ma być używana dla tej konfiguracji usługi, a następnie wybierz przycisk **OK**.

    Nowy plik konfiguracji usługi o nazwie ServiceConfiguration. [Nowa nazwa]. cscfg zostanie dodana do projektu platformy Azure w Eksplorator rozwiązań.

### <a name="to-delete-a-service-configuration"></a>Aby usunąć konfigurację usługi
1. W Eksplorator rozwiązań otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz pozycję **Zarządzaj konfiguracjami**.

    Zostanie wyświetlone okno dialogowe **Zarządzanie konfiguracjami usług** .
2. Aby usunąć konfigurację usługi, wybierz konfigurację, która ma zostać usunięta z listy **Nazwa** , a następnie wybierz pozycję **Usuń**. Zostanie wyświetlone okno dialogowe z potwierdzeniem, że chcesz usunąć tę konfigurację.
3. Wybierz pozycję **Usuń**.

     Plik konfiguracji usługi zostanie usunięty z projektu platformy Azure w Eksplorator rozwiązań.

### <a name="to-rename-a-service-configuration"></a>Aby zmienić nazwę konfiguracji usługi
1. W Eksplorator rozwiązań otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz pozycję **Zarządzaj konfiguracjami**.

    Zostanie wyświetlone okno dialogowe **Zarządzanie konfiguracjami usług** .
2. Aby zmienić nazwę konfiguracji usługi, wybierz z listy **Nazwa** nową konfigurację usługi, a następnie wybierz pozycję **Zmień nazwę**. W polu tekstowym **Nazwa** wpisz nazwę, która ma być używana dla tej konfiguracji usługi, a następnie wybierz przycisk **OK**.

    Nazwa pliku konfiguracji usługi została zmieniona w projekcie platformy Azure w Eksplorator rozwiązań.

### <a name="to-change-a-service-configuration"></a>Aby zmienić konfigurację usługi
* Jeśli chcesz zmienić konfigurację usługi, otwórz menu skrótów dla określonej roli, którą chcesz zmienić w projekcie platformy Azure, a następnie wybierz pozycję **Właściwości**. Zobacz [How to: Skonfiguruj role dla usługi w chmurze platformy Azure za pomocą programu](vs-azure-tools-configure-roles-for-cloud-service.md) Visual Studio, aby uzyskać więcej informacji.

## <a name="make-different-setting-combinations-by-using-profiles"></a>Ustawianie różnych kombinacji ustawień przy użyciu profilów
Korzystając z profilu, można automatycznie wypełnić **Kreatora publikacji** różnymi kombinacjami ustawień do różnych celów. Na przykład można mieć jeden profil do debugowania i drugi dla kompilacji wydań. W takim przypadku Twój profil **debugowania** będzie **IntelliTrace** włączony i wybrana konfiguracja **debugowania** , a Twój profil **wydania** będzie **IntelliTrace** wyłączony i konfiguracja **wydania** niezaznaczone. Można również użyć różnych profilów do wdrożenia usługi przy użyciu innego konta magazynu.

Po pierwszym uruchomieniu kreatora zostanie utworzony profil domyślny. Program Visual Studio przechowuje profil w pliku z rozszerzeniem. azurePubXml, które jest dodawane do projektu platformy Azure w folderze **Profile** . Jeśli ręcznie określisz różne opcje po uruchomieniu kreatora później, plik zostanie automatycznie zaktualizowany. Przed uruchomieniem poniższej procedury należy wcześniej opublikować usługę w chmurze co najmniej raz.

### <a name="to-add-a-profile"></a>Aby dodać profil
1. Otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz pozycję **Publikuj**.
2. Obok listy **profil docelowy** wybierz przycisk **Zapisz profil** , jak pokazano na poniższej ilustracji. Spowoduje to utworzenie profilu.

    ![Utwórz nowy profil](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/create-new-profile.png)
3. Po utworzeniu profilu wybierz pozycję **< Zarządzaj... >** na liście **profil docelowy** .

    Zostanie wyświetlone okno dialogowe **Zarządzaj profilami** , jak pokazano na poniższej ilustracji.

    ![Okno dialogowe Zarządzanie profilami](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-profiles.png)
4. Na liście **Nazwa** wybierz profil, a następnie wybierz pozycję **Utwórz kopię**.
5. Wybierz przycisk **Zamknij** .

    Nowy profil zostanie wyświetlony na liście profil docelowy.
6. Z listy **profil docelowy** wybierz właśnie utworzony profil. Ustawienia Kreatora publikacji są wypełniane przy użyciu opcji wybranych w wybranym profilu.
7. Wybierz przyciski **poprzednie** i **następne** , aby wyświetlić każdą stronę Kreatora publikacji, a następnie dostosuj ustawienia dla tego profilu. Aby uzyskać więcej informacji, zobacz [Kreator publikowania aplikacji platformy Azure](http://go.microsoft.com/fwlink/p/?LinkID=623085) .
8. Po zakończeniu dostosowywania ustawień wybierz pozycję **dalej** , aby wrócić do strony ustawień. Profil jest zapisywany podczas publikowania usługi przy użyciu tych ustawień lub po wybraniu pozycji **Zapisz** obok listy profilów.

### <a name="to-rename-or-delete-a-profile"></a>Aby zmienić nazwę profilu lub usunąć go
1. Otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz pozycję **Publikuj**.
2. Na liście **profil docelowy** wybierz pozycję **Zarządzaj**.
3. W oknie dialogowym **Zarządzanie profilami** wybierz profil, który chcesz usunąć, a następnie wybierz pozycję **Usuń**.
4. W wyświetlonym oknie dialogowym potwierdzenia wybierz pozycję **OK**.
5. Wybierz pozycję **Zamknij**.

### <a name="to-change-a-profile"></a>Aby zmienić profil
1. Otwórz menu skrótów dla projektu platformy Azure, a następnie wybierz pozycję **Publikuj**.
2. Z listy **profil docelowy** wybierz profil, który chcesz zmienić.
3. Wybierz przyciski **poprzednie** i **następne** , aby wyświetlić każdą stronę Kreatora publikacji, a następnie zmień żądane ustawienia. Aby uzyskać więcej informacji, zobacz [Kreator publikowania aplikacji platformy Azure](http://go.microsoft.com/fwlink/p/?LinkID=623085) .
4. Po zmianie ustawień wybierz pozycję **dalej** , aby wrócić do strony **ustawień** .
5. (Opcjonalnie) wybierz pozycję **Publikuj** , aby opublikować usługę w chmurze przy użyciu nowych ustawień. Jeśli nie chcesz publikować usługi w chmurze w tym momencie, a Kreator publikacji zostanie zamknięty, program Visual Studio wyświetli monit z pytaniem, czy chcesz zapisać zmiany w profilu.

## <a name="next-steps"></a>Następne kroki
Aby dowiedzieć się więcej o konfigurowaniu innych części projektu platformy Azure z poziomu programu Visual Studio, zobacz [Konfigurowanie projektu platformy Azure](http://go.microsoft.com/fwlink/p/?LinkID=623075).
