---
title: Dodawanie właściwości śledzenia do definicji DSL
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a0fd1fb2bc6440b02e0aad163ee55a7a7f86807a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652288"
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>Dodawanie właściwości śledzenia do definicji języka specyficznego dla domeny

W tym instruktażu pokazano, jak dodać właściwość śledzenia do modelu domeny.

Właściwość *domeny śledzenia* jest właściwością, która może zostać zaktualizowana przez użytkownika, ale ma wartość domyślną obliczaną przy użyciu wartości innych właściwości lub elementów domeny.

Na przykład w narzędzia języka specyficznego dla domeny (narzędzia DSL) Właściwość Nazwa wyświetlana klasy domeny ma wartość domyślną, która jest obliczana przy użyciu nazwy klasy domeny, ale użytkownik może zmienić wartość w czasie projektowania lub zresetować ją do obliczonej wartości.

W tym instruktażu utworzysz język specyficzny dla domeny (DSL), który ma właściwość śledzenia przestrzeni nazw, która ma wartość domyślną na podstawie domyślnej właściwości przestrzeni nazw modelu. Aby uzyskać więcej informacji o właściwościach śledzenia, zobacz [Definiowanie właściwości śledzenia](https://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be).

- Narzędzia DSL obsługują śledzenie deskryptorów właściwości. Jednak Projektant DSL nie może być używany do dodawania właściwości śledzenia do języka. W związku z tym należy dodać kod niestandardowy w celu zdefiniowania i zaimplementowania właściwości śledzenia.

  Właściwość śledzenia ma dwa stany: śledzenie i aktualizowanie przez użytkownika. Właściwości śledzenia mają następujące funkcje:

- W przypadku stanu śledzenia wartość właściwości śledzenia jest obliczana, a wartość jest aktualizowana w miarę zmiany innych właściwości w modelu.

- Gdy w stanie zaktualizowane przez użytkownika wartość właściwości śledzenie zachowuje wartość, do której użytkownik ostatnio ustawił właściwość.

- W oknie **Właściwości** , polecenie **Reset** dla właściwości śledzenie jest włączone tylko wtedy, gdy właściwość jest w stanie zaktualizowane przez użytkownika. **Zresetuj** polecenie ustawia stan właściwości śledzenia na śledzenie.

- W oknie **Właściwości** , gdy właściwość śledzenie jest w stanie śledzenia, jej wartość jest wyświetlana w zwykłej czcionce.

- W oknie **Właściwości** , gdy właściwość śledzenie jest w stanie zaktualizowane przez użytkownika, jej wartość jest wyświetlana w postaci pogrubionej czcionki.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu należy najpierw zainstalować następujące składniki:

| | |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580) |
| [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581) |

## <a name="create-the-project"></a>Utwórz projekt

1. Utwórz projekt projektant języka specyficznego dla domeny. Nadaj mu nazwę `TrackingPropertyDSL`.

2. W **kreatorze Projektant języka specyficznego dla domeny**ustaw następujące opcje:

    1. Wybierz szablon **MinimalLanguage** .

    2. Użyj domyślnej nazwy dla języka specyficznego dla domeny `TrackingPropertyDSL`.

    3. Ustaw rozszerzenie dla plików modelu na `trackingPropertyDsl`.

    4. Użyj domyślnej ikony szablonów dla plików modelu.

    5. Ustaw nazwę produktu do `Product Name`.

    6. Ustaw nazwę firmy na `Company Name`.

    7. Użyj wartości domyślnej dla głównej przestrzeni nazw dla projektów w rozwiązaniu, `CompanyName.ProductName.TrackingPropertyDSL`.

    8. Zezwól kreatorowi na utworzenie pliku klucza o silnej nazwie dla zestawów.

    9. Przejrzyj szczegóły rozwiązania, a następnie kliknij przycisk **Zakończ** , aby utworzyć projekt definicji DSL.

## <a name="customize-the-default-dsl-definition"></a>Dostosowywanie domyślnej definicji DSL
 W tej sekcji dostosowujesz definicję DSL, aby zawierała następujące elementy:

- Właściwość śledzenia przestrzeni nazw dla każdego elementu modelu.

- Logiczna właściwość IsNamespaceTracking dla każdego elementu modelu. Ta właściwość wskazuje, czy właściwość śledzenia jest w stanie śledzenia czy w zaktualizowanym stanie użytkownika.

- Domyślna właściwość przestrzeni nazw dla modelu. Ta właściwość będzie używana do obliczania wartości domyślnej właściwości śledzenie przestrzeni nazw.

- Właściwość obliczeniowa CustomElements dla modelu. Ta właściwość wskazuje proporcję elementów, które mają niestandardową przestrzeń nazw.

### <a name="to-add-the-domain-properties"></a>Aby dodać właściwości domeny

1. W projektancie DSL kliknij prawym przyciskiem myszy klasę **ExampleModel** domeny, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **DomainProperty**.

    1. Nazwij nową właściwość `DefaultNamespace`.

    2. W oknie **Właściwości** nowej właściwości, ustaw **wartość domyślną** na `DefaultNamespace` i ustaw dla opcji **Typ** **ciąg**.

2. Do klasy domeny **ExampleModel** Dodaj właściwość domeny o nazwie `CustomElements`.

     W oknie **Właściwości** dla nowej właściwości ustaw wartość **Typ** na **obliczone**.

3. Na **przykład** klasy domeny, Dodaj właściwość domeny o nazwie `Namespace`.

     W oknie **Właściwości** dla nowej właściwości ustaw wartość **umożliwia przeglądania** na **Fałsz**, a ustawienie **Typ** na **CustomStorage**.

4. Na **przykład** klasy domeny, Dodaj właściwość domeny o nazwie `IsNamespaceTracking`.

     W oknie **Właściwości** dla nowej właściwości ustaw wartość **umożliwia przeglądania** na **false**, ustawienie **wartości domyślnej** na `true` i ustawienie **Typ** na **wartość logiczna**.

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Aby zaktualizować elementy diagramu i szczegóły języka DSL

1. W projektancie DSL kliknij prawym przyciskiem myszy kształt geometrii **ExampleShape** , wskaż polecenie **Dodaj**, a następnie kliknij polecenie **dekoratora tekstu**.

    1. Nazwij nowy tekst dekoratora `NamespaceDecorator`.

    2. W oknie **Właściwości** dekoratora tekstu Ustaw **pozycję pozycja** na **InnerBottomLeft**.

2. W projektancie DSL wybierz wiersz, który łączy klasę **example** do kształtu **ExampleShape** .

    1. W oknie **Szczegóły DSL** wybierz kartę **mapy dekoratora** .

    2. Na liście **dekoratory** wybierz opcję **NamespaceDecorator**, zaznacz pole wyboru, a następnie na liście **właściwości wyświetlania** wybierz pozycję **przestrzeń nazw**.

3. W **Eksploratorze DSL**rozwiń folder **klasy domeny** , kliknij prawym przyciskiem myszy węzeł **przykładElement** , a następnie kliknij pozycję **Dodaj nowy deskryptor typu domeny**.

    1. Rozwiń węzeł **example** , a następnie wybierz węzeł **niestandardowy deskryptor typu (domena typu deskryptora)** .

    2. W oknie **Właściwości** deskryptora typu domeny ustaw **niestandardową** **wartość true**.

4. W **Eksploratorze DSL**wybierz węzeł **zachowanie serializacji XML** .

    1. W oknie **Właściwości** Ustaw **niestandardowe obciążenie post** na **wartość true**.

## <a name="transform-templates"></a>Przekształć szablony

Po zdefiniowaniu klas domeny i właściwości dla DSL można sprawdzić, czy Definicja DSL może być prawidłowo przekształcona w celu ponownego wygenerowania kodu dla projektu.

1. Na pasku narzędzi **Eksplorator rozwiązań** kliknij pozycję **Przekształć wszystkie szablony**.

2. System ponownie generuje kod dla rozwiązania i zapisuje DslDefinition. DSL. Aby uzyskać informacje na temat formatu XML plików definicji, zobacz [plik DslDefinition. DSL](../modeling/the-dsldefinition-dsl-file.md).

## <a name="create-files-for-custom-code"></a>Tworzenie plików dla niestandardowego kodu

Podczas przekształcania wszystkich szablonów system generuje kod źródłowy, który definiuje język specyficzny dla domeny w projektach DSL i DslPackage. Dzięki temu można uniknąć zakłócania wygenerowanego tekstu, napisać kod niestandardowy w plikach, które są odrębne od wygenerowanych plików kodu.

Musisz podać kod do obsługi wartości i stanu właściwości śledzenia. Aby ułatwić odróżnienie niestandardowego kodu od wygenerowanego kodu i uniknąć konfliktów nazw plików, należy umieścić pliki kodu niestandardowego w osobnym podfolderze.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **DSL** , wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Nowy folder**. Nadaj nazwę nowemu folderowi `CustomCode`.

2. Kliknij prawym przyciskiem myszy nowy folder **atrybut CustomCode** , wskaż polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**.

3. Wybierz szablon **pliku kodu** , ustaw **nazwę** na `NamespaceTrackingProperty.cs`, a następnie kliknij przycisk **OK**.

     Plik NamespaceTrackingProperty.cs jest tworzony i otwierany do edycji.

4. W folderze Utwórz następujące pliki kodu: `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs` i `TypeDescriptor.cs`.

5. W projekcie **DslPackage** , Utwórz również folder `CustomCode` i Dodaj do niego plik `Package.cs` kodu.

## <a name="add-helper-classes-to-support-tracking-properties"></a>Dodawanie klas pomocnika do obsługi właściwości śledzenia

Do pliku HelperClasses.cs Dodaj klasy `TrackingHelper` i `CriticalException` w następujący sposób. Te klasy zostaną odwołane w dalszej części tego przewodnika.

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

## <a name="add-custom-code-for-the-custom-type-descriptor"></a>Dodaj niestandardowy kod dla deskryptora typu niestandardowego

Zaimplementuj metodę `GetCustomProperties` dla deskryptora typu dla klasy `ExampleModel` domeny.

> [!NOTE]
> Kod generowany przez narzędzia DSL dla deskryptora typu niestandardowego dla wywołań `ExampleModel` `GetCustomProperties`; Jednak narzędzia DSL nie generują kodu, który implementuje metodę.

Zdefiniowanie tej metody powoduje utworzenie deskryptora właściwości śledzenia dla właściwości śledzenia przestrzeni nazw. Ponadto, podanie atrybutów dla właściwości śledzenia pozwala na prawidłowe wyświetlanie właściwości w oknie **Właściwości** .

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

## <a name="adding-custom-code-for-the-package"></a>Dodawanie niestandardowego kodu dla pakietu

Wygenerowany kod definiuje dostawcę opisu typu dla przykładowej klasy domeny; należy jednak dodać kod, aby nakazać DSL użycie tego dostawcy opisu typu.

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

## <a name="add-custom-code-for-the-model"></a>Dodawanie niestandardowego kodu dla modelu

Zaimplementuj metodę `GetCustomElementsValue` dla klasy domeny `ExampleModel`.

> [!NOTE]
> Kod, który generuje narzędzia DSL dla `ExampleModel` wywołań `GetCustomElementsValue`; Jednak narzędzia DSL nie generują kodu, który implementuje metodę.

Zdefiniowanie metody `GetCustomElementsValue` udostępnia logikę dla właściwości obliczeniowej CustomElements `ExampleModel`. Ta metoda zlicza `ExampleElement` klas domen, które mają właściwość śledzenia przestrzeni nazw, która ma wartość zaktualizowaną przez użytkownika, i zwraca ciąg, który reprezentuje tę liczbę jako część łącznej liczby elementów w modelu.

Dodatkowo Dodaj metodę `OnDefaultNamespaceChanged` do `ExampleModel` i Zastąp metodę `OnValueChanged` `DefaultNamespacePropertyHandler` zagnieżdżonej klasy `ExampleModel`, aby wywołać `OnDefaultNamespaceChanged`.

Ponieważ właściwość DefaultNamespace jest używana do obliczania właściwości śledzenia przestrzeni nazw, `ExampleModel` musi powiadomić wszystkie `ExampleElement` klasy domeny o zmianie wartości DefaultNamespace.

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Aby zmodyfikować procedurę obsługi właściwości dla śledzonej właściwości

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

## <a name="add-custom-code-for-the-tracking-property"></a>Dodawanie niestandardowego kodu dla właściwości śledzenia

Dodaj metodę `CalculateNamespace` do klasy `ExampleElement` domeny.

Zdefiniowanie tej metody zapewnia logikę dla właściwości obliczeniowej CustomElements `ExampleModel`. Ta metoda zlicza `ExampleElement` klas domen, które mają właściwość śledzenia przestrzeni nazw, która znajduje się w stanie zaktualizowane przez użytkownika, i zwraca ciąg, który reprezentuje tę liczbę jako część łącznej liczby elementów w modelu.

Ponadto Dodaj magazyn dla i metody, aby uzyskać i ustawić właściwość przestrzeń nazw Custom magazynu klasy `ExampleElement` domeny.

> [!NOTE]
> Kod generowany przez narzędzia DSL dla `ExampleModel` wywołuje metody get i Set; Jednak narzędzia DSL nie generują kodu, który implementuje metody.

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

## <a name="add-custom-code-to-support-serialization"></a>Dodawanie niestandardowego kodu do obsługi serializacji

Dodaj kod obsługujący niestandardowe zachowanie po ładowaniu dla serializacji XML.

> [!NOTE]
> Kod, który generuje narzędzia DSL, wywołuje metody `OnPostLoadModel` i `OnPostLoadModelAndDiagram`; Jednak narzędzia DSL nie generują kodu, który implementuje te metody.

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Aby dodać kod do obsługi niestandardowego zachowania po załadowaniu

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

Następnym krokiem jest skompilowanie i uruchomienie projektanta DSL w nowym wystąpieniu [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], aby można było sprawdzić, czy właściwość śledzenia działa poprawnie.

1. W menu **kompilacja** kliknij polecenie **Kompiluj ponownie rozwiązanie**.

2. W menu **debugowanie** kliknij **Rozpocznij debugowanie**.

    Eksperymentalna kompilacja [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] otwiera rozwiązanie **debugowania** , które zawiera pusty plik testowy.

3. W **Eksplorator rozwiązań**kliknij dwukrotnie plik test. trackingPropertyDsl, aby otworzyć go w projektancie, a następnie kliknij powierzchnię projektu.

    Zwróć uwagę, że w oknie **Właściwości** dla diagramu, **domyślna właściwość przestrzeni nazw** to **DefaultNamespace**, a właściwość **elementy niestandardowe** to **0/0**.

4. Przeciągnij element **example** z **przybornika** na powierzchnię diagramu.

5. W oknie **Właściwości** dla elementu wybierz właściwość **przestrzeń nazw elementu** i zmień wartość z **DefaultNamespace** na **OtherNamespace**.

    Zauważ, że wartość **przestrzeni nazw elementu** jest teraz pokazywana pogrubioną czcionką.

6. W oknie **Właściwości** kliknij prawym przyciskiem myszy **element przestrzeń nazw**, a następnie kliknij polecenie **Zresetuj**.

    Wartość właściwości jest zmieniana na **DefaultNamespace**, a wartość jest wyświetlana w zwykłej czcionce.

    Ponownie kliknij prawym przyciskiem myszy **element Namespace** . Polecenie **Reset** jest teraz wyłączone, ponieważ właściwość jest obecnie w stanie śledzenia.

7. Przeciągnij inny **przykładElement** z **przybornika** na powierzchnię diagramu i zmień jego **przestrzeń nazw elementu** na **OtherNamespace**.

8. Kliknij powierzchnię projektu.

    W oknie **Właściwości** diagramu wartość **elementów niestandardowych** jest teraz **1/2**.

9. Zmień **domyślną przestrzeń nazw** dla diagramu z **DefaultNamespace** na **NewNamespace**.

     **Przestrzeń nazw** pierwszego elementu śledzi **domyślną właściwość przestrzeni nazw** , podczas gdy **przestrzeń nazw** drugiego elementu zachowuje jego wartość zaktualizowaną przez użytkownika ( **OtherNamespace**).

10. Zapisz rozwiązanie, a następnie zamknij kompilację eksperymentalną.

## <a name="next-steps"></a>Następne kroki

Jeśli planujesz użycie więcej niż jednej właściwości śledzenia lub Zaimplementuj właściwości śledzenia w więcej niż jednym DSL, możesz utworzyć szablon tekstowy w celu wygenerowania wspólnego kodu do obsługi każdej właściwości śledzenia. Aby uzyskać więcej informacji na temat szablonów tekstowych, zobacz [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
- [Instrukcje: Tworzenie rozwiązania języka właściwego dla domeny](../modeling/how-to-create-a-domain-specific-language-solution.md)
