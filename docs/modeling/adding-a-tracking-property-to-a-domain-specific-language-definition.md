---
title: Dodawanie właściwości śledzenia do definicji DSL
description: Dowiedz się więcej na temat właściwości domeny śledzenia i sposobu dodawania właściwości śledzenia do modelu domeny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 546636ec3de4656bf0f6480dfaa5141d38e963d6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384918"
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>Dodawanie właściwości śledzenia do definicji języka specyficznego dla domeny

W tym przewodniku pokazano, jak dodać właściwość śledzenia do modelu domeny.

Właściwość *domeny śledzenia* jest właściwością, która może zostać zaktualizowana przez użytkownika, ale ma wartość domyślną, która jest obliczana przy użyciu wartości innych właściwości lub elementów domeny.

Na przykład w narzędziach języka Domain-Specific (DSL Tools) właściwość Nazwa wyświetlana klasy domeny ma wartość domyślną, która jest obliczana przy użyciu nazwy klasy domeny, ale użytkownik może zmienić wartość w czasie projektowania lub zresetować ją do obliczonej wartości.

W tym przewodniku utworzysz język specyficzny dla domeny (DSL), który ma właściwość śledzenia przestrzeni nazw, która ma wartość domyślną na podstawie właściwości Domyślna przestrzeń nazw modelu. Aby uzyskać więcej informacji na temat właściwości śledzenia, [zobacz Definiowanie właściwości śledzenia](/previous-versions/cc825929(v=vs.100)).

- Narzędzia DSL obsługują deskryptory właściwości śledzenia. Jednak projektant DSL nie może służyć do dodawania właściwości śledzenia do języka. W związku z tym należy dodać kod niestandardowy, aby zdefiniować i zaimplementować właściwość śledzenia.

  Właściwość śledzenia ma dwa stany: śledzenie i aktualizacja przez użytkownika. Właściwości śledzenia mają następujące funkcje:

- W stanie śledzenia obliczana jest wartość właściwości śledzenia, a wartość jest aktualizowana w przypadku zmiany innych właściwości w modelu.

- W przypadku aktualizacji według stanu użytkownika wartość właściwości śledzenia zachowuje wartość, na którą użytkownik ostatnio ustawił właściwość.

- W **oknie** Właściwości polecenie **Resetuj** dla właściwości śledzenia jest włączone tylko wtedy, gdy właściwość jest w stanie zaktualizowanym przez użytkownika. Polecenie **Reset** ustawia stan właściwości śledzenia na śledzenie.

- Gdy **właściwość** śledzenia jest w stanie śledzenia, w oknie Właściwości jest wyświetlana zwykła czcionka.

- W **oknie** Właściwości, gdy właściwość śledzenia jest aktualizowana według stanu użytkownika, jej wartość jest wyświetlana czcionką pogrubioną.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem pracy z tym instruktażem należy najpierw zainstalować następujące składniki:

| Składnik | Link |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkID=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true) |
| [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185581](https://code.msdn.microsoft.com/site/search?query=%22Modeling%20SDK%22&f%5B0%5D.Value=%22Modeling%20SDK%22&f%5B0%5D.Type=SearchText&ac=5) |

## <a name="create-the-project"></a>Tworzenie projektu

1. Utwórz projekt Domain-Specific Language Designer. Nadaj jej nazwę `TrackingPropertyDSL`.

2. W **kreatorze projektant języka specyficznego dla domeny** ustaw następujące opcje:

    1. Wybierz szablon **MinimalLanguage.**

    2. Użyj domyślnej nazwy języka specyficznego dla domeny, `TrackingPropertyDSL` .

    3. Ustaw rozszerzenie dla plików modelu na `trackingPropertyDsl` wartość .

    4. Użyj domyślnej ikony szablonu dla plików modelu.

    5. Ustaw nazwę produktu na `Product Name` .

    6. Ustaw nazwę firmy na `Company Name` .

    7. Użyj wartości domyślnej dla głównej przestrzeni nazw dla projektów w `CompanyName.ProductName.TrackingPropertyDSL` rozwiązaniu .

    8. Zezwalaj kreatorowi na utworzenie pliku klucza silnej nazwy dla zestawów.

    9. Przejrzyj szczegóły rozwiązania, a następnie kliknij przycisk **Zakończ,** aby utworzyć projekt definicji DSL.

## <a name="customize-the-default-dsl-definition"></a>Dostosowywanie domyślnej definicji DSL
 W tej sekcji dostosujemy definicję DSL tak, aby zawierała następujące elementy:

- Właściwość śledzenia przestrzeni nazw dla każdego elementu modelu.

- Właściwość Boolean IsNamespaceTracking dla każdego elementu modelu. Ta właściwość wskaże, czy właściwość śledzenia jest w stanie śledzenia, czy jest aktualizowana według stanu użytkownika.

- Właściwość Default Namespace (Domyślna przestrzeń nazw) dla modelu. Ta właściwość będzie używana do obliczania wartości domyślnej właściwości Śledzenie przestrzeni nazw.

- Właściwość obliczeniowa CustomElements dla modelu. Ta właściwość będzie wskazywać proporcję elementów, które mają niestandardową przestrzeń nazw.

### <a name="to-add-the-domain-properties"></a>Aby dodać właściwości domeny

1. W projektancie DSL kliknij prawym przyciskiem myszy **klasę domeny ExampleModel,** wskaż polecenie **Dodaj**, a następnie kliknij pozycję **DomainProperty**.

    1. Nadaj nowej właściwości nazwę `DefaultNamespace` .

    2. W **oknie Właściwości** dla nowej właściwości ustaw wartość **Wartość** domyślna na , a dla ustawienia `DefaultNamespace` Typ **ustaw** wartość **Ciąg**.

2. Do klasy **domeny ExampleModel** dodaj właściwość domeny o nazwie `CustomElements` .

     W **oknie Właściwości** dla nowej właściwości ustaw dla ustawienia **Rodzaj** wartość **Obliczony**.

3. Do klasy **domeny ExampleElement** dodaj właściwość domeny o nazwie `Namespace` .

     W **oknie Właściwości** dla nowej właściwości ustaw wartość **Fałsz** na Wartość Przeglądania, a dla ustawienia **Rodzaj** ustaw wartość **CustomStorage.**

4. Do klasy **domeny ExampleElement** dodaj właściwość domeny o nazwie `IsNamespaceTracking` .

     W **oknie** Właściwości dla nowej  właściwości ustaw wartość  Fałsz dla właściwości **Przeglądanie,** ustaw wartość Wartość domyślna na , a dla ustawienia `true` **Typ** ustaw wartość **logiczną**.

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Aby zaktualizować elementy diagramu i szczegóły DSL

1. W projektancie DSL kliknij prawym przyciskiem myszy kształt **geometrii ExampleShape,** wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Dekorator tekstu.**

    1. Nadaj nowej nazwie dekorator tekstu `NamespaceDecorator` .

    2. W **oknie Właściwości** dla dekoratora tekstu ustaw pozycję **Position na** **InnerBottomLeft**.

2. W projektancie DSL wybierz wiersz, który łączy **klasę ExampleElement** z **kształtem ExampleShape.**

    1. W **oknie Szczegóły DSL** wybierz **kartę Mapy dekoratora.**

    2. Na liście **Decorators (Dekoratory)** wybierz pozycję **NamespaceDecorator**,zaznacz jego pole wyboru, a następnie na liście **właściwości Display** (Wyświetl właściwości) wybierz pozycję **Namespace (Przestrzeń nazw).**

3. W **Eksploratorze DSL** rozwiń folder **Klasy** domen, kliknij prawym przyciskiem myszy węzeł **ExampleElement,** a następnie kliknij polecenie Dodaj nowy deskryptor **typu domeny**.

    1. Rozwiń **węzeł ExampleElement** i wybierz węzeł Deskryptor typu niestandardowego **(Deskryptor typu domeny).**

    2. W **oknie** Właściwości deskryptora typu domeny ustaw wartość **Prawda dla opcji Kodowane niestandardowe.**

4. W **Eksploratorze DSL** wybierz **węzeł Zachowanie serializacji XML.**

    1. W **oknie Właściwości** ustaw wartość **True dla opcji Niestandardowe ładowanie** **wpisów.**

## <a name="transform-templates"></a>Przekształcanie szablonów

Teraz, po zdefiniowaniu klas i właściwości domeny dla DSL, możesz sprawdzić, czy definicja DSL może zostać poprawnie przekształcona w celu ponownego wygenerowania kodu dla projektu.

1. Na pasku **Eksplorator rozwiązań** kliknij pozycję **Przekształć wszystkie szablony.**

2. System ponownie generuje kod rozwiązania i zapisuje dslDefinition.dsl. Aby uzyskać informacje o formacie XML plików definicji, zobacz [Plik DslDefinition.dsl](../modeling/the-dsldefinition-dsl-file.md).

## <a name="create-files-for-custom-code"></a>Tworzenie plików dla kodu niestandardowego

Podczas przekształcania wszystkich szablonów system generuje kod źródłowy, który definiuje język specyficzny dla domeny w projektach Dsl i DslPackage. Aby uniknąć zakłócania wygenerowanego tekstu, napisz kod niestandardowy w plikach, które różnią się od wygenerowanych plików kodu.

Należy podać kod do obsługi wartości i stanu właściwości śledzenia. Aby ułatwić odróżnienie kodu niestandardowego od wygenerowanego kodu i uniknąć konfliktów nazw plików, umieść niestandardowe pliki kodu w oddzielnym podfolderze.

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **DSL,** wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Nowy folder**. Nazwij nowy folder `CustomCode` .

2. Kliknij prawym przyciskiem myszy nowy folder **CustomCode,** wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Nowy element**.

3. Wybierz szablon **Plik kodu,** ustaw wartość **pola Nazwa** na , a następnie kliknij `NamespaceTrackingProperty.cs` przycisk **OK.**

     Plik NamespaceTrackingProperty.cs zostanie utworzony i otwarty do edycji.

4. W folderze utwórz następujące pliki kodu: `ExampleModel.cs,``HelperClasses.cs` `Serialization.cs` , i `TypeDescriptor.cs` .

5. W **projekcie DslPackage** utwórz również folder i dodaj do niego `CustomCode` `Package.cs` plik kodu.

## <a name="add-helper-classes-to-support-tracking-properties"></a>Dodawanie klas pomocników do właściwości śledzenia obsługi

Do pliku HelperClasses.cs dodaj `TrackingHelper` klasy i w następujący `CriticalException` sposób. Odwołania do tych klas będą się odwoływać w dalszej części tego przewodnika.

1. Dodaj następujący kod do pliku HelperClasses.cs.

    ```csharp
    using System;
    using System.Collections;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        internal static class TrackingHelper
        {
            /// <summary>Notify each model element in a collection that a tracked
            /// property has changed.</summary>
            /// <param name="store">The store for the model.</param>
            /// <param name="collection">The collection of model elements that
            /// contain the tracking property.</param>
            /// <param name="propertyId">The ID of the tracking property.</param>
            /// <param name="trackingPropertyId">The ID of the property that
            /// indicates whether the tracking property is tracking.</param>
            internal static void UpdateTrackingCollectionProperty(
                Store store,
                IEnumerable collection,
                Guid propertyId,
                Guid trackingPropertyId)
            {
                DomainPropertyInfo propInfo =
                    store.DomainDataDirectory.GetDomainProperty(propertyId);

                DomainPropertyInfo trackingPropInfo =
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);

                Debug.Assert(propInfo != null);
                Debug.Assert(trackingPropInfo != null);
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),
                    "Tracking property not specified as a boolean");

                foreach (ModelElement element in collection)
                {
                    // If the tracking property is currently tracking, then notify
                    // it that the tracked property has changed.
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);
                    if (isTracking)
                    {
                        propInfo.NotifyValueChange(element);
                    }
                }
            }
        }

        /// <summary>Helper class to flag critical exceptions from ones that are
        /// safe to ignore.</summary>
        internal static class CriticalException
        {
            /// <summary>Gets whether an exception is critical and can not be
            /// ignored.</summary>
            /// <param name="ex">The exception to check.</param>
            /// <returns>True if the exception is critical.</returns>
            internal static bool IsCriticalException(Exception ex)
            {
                if (ex is NullReferenceException
                    || ex is StackOverflowException
                    || ex is OutOfMemoryException
                    || ex is System.Threading.ThreadAbortException)
                    return true;

                if (ex.InnerException != null)
                    return IsCriticalException(ex.InnerException);

                return false;
            }
        }
    }
    ```

## <a name="add-custom-code-for-the-custom-type-descriptor"></a>Dodawanie kodu niestandardowego dla deskryptora typów niestandardowych

`GetCustomProperties`Zaim implementuj metodę dla deskryptora typu `ExampleModel` dla klasy domeny.

> [!NOTE]
> Kod generowany przez narzędzia DSL dla deskryptora typu niestandardowego dla wywołań; jednak narzędzia DSL nie generują kodu, który `ExampleModel` `GetCustomProperties` implementuje metodę .

Zdefiniowanie tej metody powoduje utworzenie deskryptora właściwości śledzenia dla właściwości śledzenia przestrzeni nazw. Ponadto podanie atrybutów dla właściwości śledzenia umożliwia **prawidłowe** wyświetlanie właściwości w oknie Właściwości.

### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Aby zmodyfikować deskryptor typu dla klasy domeny ExampleModel

1. Dodaj następujący kod do pliku TypeDescriptor.cs.

    ```csharp
    using System;
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the custom type descriptor for the ExampleElement domain class, add
        // the GetCustomProperties method.
        public partial class ExampleElementTypeDescriptor
        {
            /// <summary>Returns the property descriptors for the described
            /// ExampleElement domain class.</summary>
            /// <remarks>This method adds the tracking property descriptor.
            /// </remarks>
            private PropertyDescriptorCollection GetCustomProperties(
                Attribute[] attributes)
            {
                // Get the default property descriptors from the base class
                PropertyDescriptorCollection propertyDescriptors =
                    base.GetProperties(attributes);

                // Get a reference to the model element that is being described.
                ExampleElement source = this.ModelElement as ExampleElement;

                //Add the descriptor for the tracking property.
                if (source != null)
                {
                    DomainPropertyInfo domainProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.NamespaceDomainPropertyId);

                    DomainPropertyInfo trackingProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);

                    // Define attributes for the tracking property so that the
                    // Properties window displays the property correctly.
                    Attribute[] attr = new Attribute[] {
                        new DisplayNameAttribute("Element Namespace"),
                        new DescriptionAttribute("The namespace of the element."),
                        new CategoryAttribute("Tracking Properties"),
                    };

                    propertyDescriptors.Add(new TrackingPropertyDescriptor(
                        source, domainProperty, trackingProperty, attr));
                }

                // Return the property descriptors for this element
                return propertyDescriptors;
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-package"></a>Dodawanie kodu niestandardowego dla pakietu

Wygenerowany kod definiuje dostawcę opisu typu dla klasy domeny ExampleElement; Należy jednak dodać kod, aby poinstruować DSL, aby użyć tego dostawcy opisu typu.

1. Dodaj następujący kod do pliku Package.cs.

    ```csharp
    using System.ComponentModel;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // Override the default Initialize method.
        internal sealed partial class TrackingPropertyDSLPackage
        {
            protected override void Initialize()
            {
                // Add the custom type descriptor for the ExampleElement type.
                TypeDescriptor.AddProvider(
                    new ExampleElementTypeDescriptionProvider(),
                    typeof(ExampleElement));

                base.Initialize();
            }
        }
    }
    ```

## <a name="add-custom-code-for-the-model"></a>Dodawanie kodu niestandardowego dla modelu

`GetCustomElementsValue`Zaim implementuj metodę `ExampleModel` dla klasy domeny.

> [!NOTE]
> Kod generowany przez narzędzia DSL dla wywołań ; jednak narzędzia DSL nie generują kodu, `ExampleModel` `GetCustomElementsValue` który implementuje metodę .

Zdefiniowanie `GetCustomElementsValue` metody zapewnia logikę dla właściwości obliczeniowej CustomElements elementu `ExampleModel` . Ta metoda zlicza klasy domen, które mają właściwość śledzenia przestrzeni nazw, która ma wartość zaktualizowaną przez użytkownika, i zwraca ciąg reprezentujący tę liczbę jako część całkowitej liczby elementów w `ExampleElement` modelu.

Ponadto dodaj metodę do metody i zastąp metodę zagnieżdżonych klas w celu `OnDefaultNamespaceChanged` `ExampleModel` wywołania metody `OnValueChanged` `DefaultNamespacePropertyHandler` `ExampleModel` `OnDefaultNamespaceChanged` .

Ponieważ właściwość DefaultNamespace jest używana do obliczania właściwości śledzenia przestrzeni nazw, musi powiadomić wszystkie klasy domeny, że wartość `ExampleModel` `ExampleElement` DefaultNamespace została zmieniona.

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Aby zmodyfikować program obsługi właściwości dla śledzone właściwości

1. Dodaj następujący kod do pliku ExampleModel.cs.

    ```csharp
    using System.Linq;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        public partial class ExampleModel
        {
            public string GetCustomElementsValue()
            {
                if (this.Elements.Count == 0) return "0/0";

                int number = this.Elements.Count(e => !e.IsNamespaceTracking);
                return string.Format("{0}/{1}", number, this.Elements.Count);
            }

            #region Value changed handler for the tracked property

            // When a tracked property changes, it needs to notify all of the properties
            // that track it.

            /// <summary>Called by the DefaultNamespace property value handler when the
            /// DefaultNamespace property changes.</summary>
            /// <param name="oldValue">The previous value of the property.</param>
            /// <param name="newValue">The new value of the property.</param>
            protected virtual void OnDefaultNamespaceChanged(
                string oldValue, string newValue)
            {
                // Use the helper class to notify all of the elements in the model
                // that the default namespace has changed.
                TrackingHelper.UpdateTrackingCollectionProperty(
                    this.Store,
                    this.Elements,
                    ExampleElement.NamespaceDomainPropertyId,
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);
            }

            // Update the change handler for the DefaultNamespace property.
            internal sealed partial class DefaultNamespacePropertyHandler
            {
                /// <summary>Called when the DefaultNamespace property changes.</summary>
                /// <param name="element">The model element that has the property that
                /// changed.</param>
                /// <param name="oldValue">The previous value of the property.</param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleModel element, string oldValue, string newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);

                    if (!element.Store.InUndoRedoOrRollback)
                    {
                        element.OnDefaultNamespaceChanged(oldValue, newValue);
                    }
                }
            }

            #endregion
        }
    }
    ```

## <a name="add-custom-code-for-the-tracking-property"></a>Dodawanie kodu niestandardowego dla właściwości śledzenia

Dodaj `CalculateNamespace` metodę do `ExampleElement` klasy domeny.

Zdefiniowanie tej metody zapewnia logikę właściwości obliczeniowej CustomElements elementu `ExampleModel` . Ta metoda zlicza klasy domen, które mają właściwość śledzenia przestrzeni nazw, która jest aktualizowana według stanu użytkownika, i zwraca ciąg reprezentujący tę liczbę jako część całkowitej liczby elementów w `ExampleElement` modelu.

Ponadto dodaj magazyn dla metod i , aby pobrać i ustawić niestandardową właściwość Magazynu przestrzeni nazw `ExampleElement` klasy domeny.

> [!NOTE]
> Kod, który są generowane przez narzędzia DSL dla wywołuje metody get i set, jednak narzędzia DSL nie generują kodu, `ExampleModel` który implementuje metody.

### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Aby dodać metodę dla deskryptora typu niestandardowego

1. Dodaj następujący kod do pliku NamespaceTrackingProperty.cs.

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the domain class that has the tracking property, add the caluclation
        // for when the property is tracking.
        public partial class ExampleElement
        {
            /// <summary>Calculates the actual value of the property when it is
            /// tracking.</summary>
            /// <returns>The value of the tracking property when it is
            /// tracking.</returns>
            /// <remarks>Making this method virtual allows child classes to modify
            /// the calculation. This method does not need to perform validation, as
            /// its caller handles validation prior to calling this method.
            /// <para>In this case, the tracking value depends on the default namespace
            /// property of the parent model.</para></remarks>
            protected virtual string CalculateNamespace()
            {
                return this.ExampleModel.DefaultNamespace;
            }

            #region Tracking property implementation

            // Implement the Namespace domain property of the ExampleElement domain class,
            // and update the IsNamespaceTracking domain property value handler.

            /// <summary>Storage for the Namespace property.</summary>
            private string namespaceStorage;

            /// <summary>Gets the value of the Namespace property.</summary>
            /// <returns>The value of the Namespace property.</returns>
            private string GetNamespaceValue()
            {
                // Only retrieve the tracked value if the store is not in the
                // middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!loading && this.IsNamespaceTracking)
                {
                    try
                    {
                        return this.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                        return default(string);
                    }
                    catch (Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                        else
                        {
                            return default(string);
                        }
                    }
                }

                return namespaceStorage;
            }

            /// <summary>Sets the value of the Namespace property.</summary>
            /// <param name="value">The new value for the property.</param>
            private void SetNamespaceValue(string value)
            {
                namespaceStorage = value;

                // Only update the state of the tracking property if the store is
                // not in the middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!this.Store.InUndoRedoOrRollback && !loading)
                {
                    this.IsNamespaceTracking = false;
                }
            }

            // Update the default behavior of the ExampleElement.IsNamespaceTracking
            // domain property value handler.
            internal sealed partial class IsNamespaceTrackingPropertyHandler
            {
                /// <summary>Called after the IsNamespaceTracking property changes.
                /// </summary>
                /// <param name="element">The model element that has the property
                /// that changed.</param>
                /// <param name="oldValue">The previous value of the property.
                /// </param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleElement element, Boolean oldValue, Boolean newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);
                    if (!element.Store.InUndoRedoOrRollback && newValue)
                    {
                        DomainPropertyInfo propInfo =
                            element.Store.DomainDataDirectory.GetDomainProperty(
                                ExampleElement.NamespaceDomainPropertyId);
                        propInfo.NotifyValueChange(element);
                    }
                }

                /// <summary>Performs the reset operation for the IsNamespaceTracking
                /// property for a model element.</summary>
                /// <param name="element">The model element that has the property
                /// to reset.</param>
                internal void ResetValue(ExampleElement element)
                {
                    object calculatedValue = null;

                    try
                    {
                        calculatedValue = element.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                    }
                    catch (System.Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                    }

                    if ((calculatedValue != null
                        && object.Equals(element.Namespace, calculatedValue)))
                    {
                        element.isNamespaceTrackingPropertyStorage = true;
                    }
                }

                /// <summary>Method to set IsNamespaceTracking to false so that this
                /// instance of this tracking property is not storage-based.
                /// </summary>
                /// <param name="element">The element on which to reset the property
                /// value.</param>
                internal void PreResetValue(ExampleElement element)
                {
                    // Force the IsNamespaceTracking property to false so that the value
                    // of the Namespace property is retrieved from storage.
                    element.isNamespaceTrackingPropertyStorage = false;
                }
            }

            #endregion
        }
    }
    ```

## <a name="add-custom-code-to-support-serialization"></a>Dodawanie kodu niestandardowego do obsługi serializacji

Dodaj kod do obsługi niestandardowego zachowania po załadowaniu dla serializacji XML.

> [!NOTE]
> Kod, który generuje narzędzia DSL wywołuje metody i ; jednak narzędzia DSL nie generują kodu, który `OnPostLoadModel` `OnPostLoadModelAndDiagram` implementuje te metody.

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Aby dodać kod obsługujący niestandardowe zachowanie po załadowaniu

1. Dodaj następujący kod do pliku Serialization.cs.

    ```csharp
    using System;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        #region Helper classes for maintaining state while the store is serializing.

        public abstract partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Reset the tracking state properties to their natural values
            /// based on comparing storage with calculation.</summary>
            /// <param name="store">The store that contains this model.</param>
            internal static void ResetTrackingProperties(Store store)
            {
                // Two passes required - one to set all elements to storage-based
                // then another to set some back to being tracking.
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.PreResetIsTrackingProperties();
                        continue;
                    }
                }
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.ResetIsTrackingProperties();
                        continue;
                    }
                }
            }
        }

        // Add the pre-reset and reset methods for the model element.
        public partial class ExampleElement
        {
            /// <summary>Calls the pre-reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void PreResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);
            }

            /// <summary>Calls the reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void ResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);
            }
        }

        #endregion

        #region Custom serialization code

        // To the serialization helper for the TrackingPropertyDSL class, add post
        // load handlers to bind the tracking property to the serialization process.
        // These handlers manage the tracking states and property values when the
        // model is serialized and deserialized.
        public partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Customize model loading.</summary>
            /// <param name="serializationResult">The serialization result from the
            /// load operation.</param>
            /// <param name="partition">The partition in which the new
            /// instance was created.</param>
            /// <param name="fileName">The name of the file from which the
            /// instance was deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.
            /// </param>
            private void OnPostLoadModel(
                SerializationResult serializationResult,
                Partition partition,
                string fileName,
                ExampleModel modelRoot)
            {
            }

            /// <summary>Customize model and diagram loading.</summary>
            /// <param name="serializationResult">Stores serialization result from
            /// the load operation.</param>
            /// <param name="modelPartition">Partition in which the new
            /// instance will be created.</param>
            /// <param name="modelFileName">Name of the file from which the
            /// instance will be deserialized.</param>
            /// <param name="diagramPartition">Partition in which the new
            /// diagram instance will be created.</param>
            /// <param name="diagramFileName">Name of the file from which the
            /// diagram instance will be deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.</param>
            /// <param name="diagram">The diagram matching the modelRoot.</param>
            private void OnPostLoadModelAndDiagram(
                SerializationResult serializationResult,
                Partition modelPartition,
                string modelFileName,
                Partition diagramPartition,
                string diagramFileName,
                ExampleModel modelRoot,
                TrackingPropertyDSLDiagram diagram)
            {
                Debug.Assert(modelPartition != null);
                Debug.Assert(modelPartition.Store != null);

                // Tracking properties need to be set up according to whether the
                // serialization matches the calculated values.
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(
                    modelPartition.Store);
            }
        }

        #endregion
    }
    ```

## <a name="test-the-language"></a>Testowanie języka

Następnym krokiem jest skompilowanie i uruchomienie projektanta DSL w nowym wystąpieniu obiektu , aby można było sprawdzić, czy właściwość [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] śledzenia działa prawidłowo.

1. W menu **Build (Kompilacja)** kliknij pozycję **Rebuild Solution (Skompilowanie rozwiązania).**

2. W menu **Debugowanie** kliknij polecenie **Rozpocznij debugowanie**.

    Eksperymentalna kompilacja [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] narzędzia otwiera rozwiązanie **Debugowanie,** które zawiera pusty plik testowy.

3. W **Eksplorator rozwiązań** kliknij dwukrotnie plik Test.trackingPropertyDsl, aby otworzyć go w projektancie, a następnie kliknij powierzchnię projektową.

    Zwróć uwagę, że **w** oknie Właściwości diagramu właściwość **Domyślna** przestrzeń nazw to **DefaultNamespace,** a właściwość **Elementy** niestandardowe to **0/0.**

4. Przeciągnij element **ExampleElement** z **przybornika** na powierzchnię diagramu.

5. W **oknie** Właściwości elementu wybierz właściwość **Przestrzeń** nazw elementu i zmień wartość z **DefaultNamespace** na **OtherNamespace.**

    Zauważ, że wartość elementu **Przestrzeń nazw jest** teraz wyświetlana pogrubioną czcionką.

6. W **oknie Właściwości** kliknij prawym przyciskiem myszy **element Przestrzeń nazw**, a następnie kliknij polecenie **Resetuj**.

    Wartość właściwości jest zmieniana na **DefaultNamespace,** a wartość jest wyświetlana za jej czcionką zwykłą.

    Ponownie kliknij prawym **przyciskiem myszy pozycję Przestrzeń nazw** elementu. Polecenie **Reset** jest teraz wyłączone, ponieważ właściwość jest obecnie w stanie śledzenia.

7. Przeciągnij kolejny **element ExampleElement** z **przybornika** na powierzchnię diagramu i zmień jego **przestrzeń nazw elementu** na **OtherNamespace.**

8. Kliknij powierzchnię projektową.

    W **oknie** Właściwości diagramu wartość  elementów niestandardowych wynosi **teraz 1/2**.

9. Zmień **domyślną przestrzeń** nazw dla diagramu **z DefaultNamespace na** **NewNamespace.**

     Przestrzeń **nazw** pierwszego elementu śledzi właściwość **Default Namespace,** natomiast przestrzeń nazw drugiego elementu zachowuje zaktualizowaną przez użytkownika wartość elementu **OtherNamespace.** 

10. Zapisz rozwiązanie, a następnie zamknij eksperymentalną kompilację.

## <a name="next-steps"></a>Następne kroki

Jeśli planujesz używać więcej niż jednej właściwości śledzenia lub implementować właściwości śledzenia w więcej niż jednym DSL, możesz utworzyć szablon tekstowy w celu wygenerowania wspólnego kodu do obsługi każdej właściwości śledzenia. Aby uzyskać więcej informacji na temat szablonów tekstowych, zobacz [Generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
- [Instrukcje: Tworzenie rozwiązania języka właściwego dla domeny](../modeling/how-to-create-a-domain-specific-language-solution.md)