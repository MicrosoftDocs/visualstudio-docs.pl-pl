---
title: Pobieranie informacji o usłudze z magazynu ustawień | Microsoft Docs
description: Dowiedz się, jak za pomocą magazynu ustawień znaleźć wszystkie dostępne usługi lub określić, czy dana usługa jest zainstalowana.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 57a273d994e6b8a4b34a139ab98713cc8c6cd83b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968128"
---
# <a name="get-service-information-from-the-settings-store"></a>Pobierz informacje o usłudze z magazynu ustawień
Aby znaleźć wszystkie dostępne usługi lub określić, czy dana usługa jest zainstalowana, można użyć magazynu ustawień. Musisz znać typ klasy usługi.

## <a name="to-list-the-available-services"></a>Aby wyświetlić listę dostępnych usług

1. Utwórz projekt VSIX o nazwie `FindServicesExtension` , a następnie dodaj polecenie niestandardowe o nazwie `FindServicesCommand` . Aby uzyskać więcej informacji na temat tworzenia polecenia niestandardowego, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. W *FindServicesCommand.cs* Dodaj następujące dyrektywy using:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Pobierz magazyn ustawień konfiguracji, a następnie Znajdź podkolekcję o nazwie Services. Ta kolekcja zawiera wszystkie dostępne usługi. W `MenuItemCommand` metodzie usuń istniejący kod i zastąp go następującym:

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

4. Skompiluj projekt i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.

5. W eksperymentalnym wystąpieniu, w menu **Narzędzia** kliknij polecenie **Wywołaj FindServicesCommand**.

     Powinien pojawić się okno komunikatu z listą wszystkich usług.

     Aby sprawdzić te ustawienia, można użyć Edytora rejestru.

## <a name="find-a-specific-service"></a>Znajdowanie określonej usługi
 Można również użyć metody, <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> Aby określić, czy dana usługa jest zainstalowana. Musisz znać typ klasy usługi.

1. W MenuItemCallback projektu, który został utworzony w poprzedniej procedurze, Wyszukaj w magazynie ustawienia konfiguracji `Services` kolekcję, która ma podkolekcję o nazwie identyfikator GUID usługi. W takim przypadku będziemy szukać usługi pomocy.

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

2. Skompiluj projekt i Rozpocznij debugowanie.

3. W eksperymentalnym wystąpieniu, w menu **Narzędzia** kliknij polecenie **Wywołaj FindServicesCommand**.

     Powinien zostać wyświetlony komunikat z **dostępną usługą**  tekstową: po której następuje **wartość true** lub **false**. Aby sprawdzić to ustawienie, można użyć Edytora rejestru, jak pokazano w poprzednich krokach.
