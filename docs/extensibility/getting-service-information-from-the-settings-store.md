---
title: Pobieranie informacji o usłudze z Store ustawienia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe38bf84510ea247c737477e421db8dbb15f63c0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62863145"
---
# <a name="get-service-information-from-the-settings-store"></a>Uzyskaj informacje o usłudze z magazynu ustawień
Można użyć magazynu ustawień, aby znaleźć wszystkie dostępne usługi lub aby określić, czy określona usługa jest zainstalowana. Musisz znać typ klasy usługi.

## <a name="to-list-the-available-services"></a>Aby wyświetlić listę dostępnych usług

1. Utwórz projekt VSIX, o nazwie `FindServicesExtension` , a następnie dodaj polecenie niestandardowe o nazwie `FindServicesCommand`. Aby uzyskać więcej informacji na temat tworzenia niestandardowych poleceń, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. W *FindServicesCommand.cs*, Dodaj następujące instrukcje using:

    ```vb
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Pobierz magazyn ustawień konfiguracji, a następnie znajdź podkolekcję o nazwie usługi. Ta kolekcja zawiera wszystkie dostępne usługi. W `MenuItemCommand` metody, usuń istniejący kod i zastąp go następującym kodem:

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string message = "Available services:\n";
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");
        int n = 0;
        foreach (string service in collection)
        {
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";
        }

        MessageBox.Show(message);
    }
    ```

4. Skompiluj projekt, a następnie rozpocząć debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.

5. W doświadczalnym wystąpieniu na **narzędzia** menu, kliknij przycisk **wywołania FindServicesCommand**.

     Okno komunikatu, wyświetlanie listy wszystkich usług powinny być widoczne.

     Aby sprawdzić te ustawienia, można Użyj Edytora rejestru.

## <a name="find-a-specific-service"></a>Znajdź określonej usługi
 Można również użyć <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> metodę pozwala ustalić, czy określona usługa jest zainstalowana. Musisz znać typ klasy usługi.

1. Wyszukaj w sklepie ustawień konfiguracji w MenuItemCallback projekt utworzony w poprzedniej procedurze, `Services` kolekcja, która ma podkolekcję o nazwie określonej przez identyfikator GUID usługi. W takim przypadku firma Microsoft będzie szukał usługi pomocy.

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);
        string message = "Help Service Available: " + hasHelpService;

        MessageBox.Show(message);
    }
    ```

2. Skompiluj projekt, a następnie rozpocząć debugowanie.

3. W doświadczalnym wystąpieniu na **narzędzia** menu, kliknij przycisk **wywołania FindServicesCommand**.

     Powinien zostać wyświetlony komunikat z tekstem **pomocy dostępne usługi:** następuje **True** lub **False**. Aby sprawdzić to ustawienie, służy Edytor rejestru, jak pokazano w poprzednich krokach.