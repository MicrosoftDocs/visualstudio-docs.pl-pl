---
title: Uzyskiwanie informacji o usłudze z Magazynu ustawień | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b15d5c9f122ca66d21940b9998969b0d39d1a74d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711372"
---
# <a name="get-service-information-from-the-settings-store"></a>Pobierz informacje o usłudze z magazynu ustawień
Można użyć magazynu ustawień, aby znaleźć wszystkie dostępne usługi lub określić, czy dana usługa jest zainstalowana. Musisz znać typ klasy usługi.

## <a name="to-list-the-available-services"></a>Aby wyświetlić listę dostępnych usług

1. Utwórz projekt VSIX o nazwie, `FindServicesExtension` `FindServicesCommand`a następnie dodaj niestandardowe polecenie o nazwie . Aby uzyskać więcej informacji na temat tworzenia polecenia niestandardowego, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. W *FindServicesCommand.cs*dodaj następujące elementy za pomocą dyrektyw:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Pobierz magazyn ustawień konfiguracji, a następnie znajdź podkolekcję o nazwie Usługi. Ta kolekcja zawiera wszystkie dostępne usługi. W `MenuItemCommand` metodzie usuń istniejący kod i zastąp go następującymi:

    ```csharp
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

4. Skompiluj projekt i rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.

5. W wystąpieniu eksperymentalnym w menu **Narzędzia** kliknij polecenie **Wywołaj polecenie FindServicesCommand**.

     Powinno zostać wyświetlenie okna komunikatu zawierającego listę wszystkich usług.

     Aby zweryfikować te ustawienia, można użyć edytora rejestru.

## <a name="find-a-specific-service"></a>Znajdź konkretną usługę
 Można również użyć <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> metody, aby określić, czy dana usługa jest zainstalowana. Musisz znać typ klasy usługi.

1. W MenuItemCallback projektu utworzonego w poprzedniej procedurze przeszukaj magazyn `Services` ustawień konfiguracji dla kolekcji, która ma podkolekcję nazwaną identyfikatorem GUID usługi. W takim przypadku poszukamy usługi Pomocy.

    ```csharp
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

2. Skompiluj projekt i rozpocznij debugowanie.

3. W wystąpieniu eksperymentalnym w menu **Narzędzia** kliknij polecenie **Wywołaj polecenie FindServicesCommand**.

     Powinna zostać wyświetlona wiadomość z tekstem **Dostępna usługa pomocy:** po której następuje **prawda** lub **fałsz**. Aby zweryfikować to ustawienie, można użyć edytora rejestru, jak pokazano we wcześniejszych krokach.
