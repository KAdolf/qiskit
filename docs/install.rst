Installing Qiskit
=================

Requirements
------------

Qiskit supports Python 3.5 or later.

We recommend installing `Anaconda <https://www.anaconda.com/download/>`__, a
cross-platform Python distribution for scientific computing. Jupyter,
included in Anaconda, is recommended for interacting with Qiskit.

Qiskit is tested and supported on the following 64-bit systems:

*	Ubuntu 16.04 or later
*	macOS 10.12.6 or later
*	Windows 7 or later

Using Qiskit on Windows requires VC++ runtime components. We recommend one of
the following:

* `Microsoft Visual C++ Redistributable for Visual Studio 2017 <https://
  go.microsoft.com/fwlink/?LinkId=746572>`__
* `Microsoft Visual C++ Redistributable for Visual Studio 2015 <https://
  www.microsoft.com/en-US/download/details.aspx?id=48145>`__


Install
-------

We recommend using Python virtual environments to cleanly separate Qiskit from
other applications and improve your experience.

The simplest way to use environments is by using the ``conda`` command,
included with Anaconda. A Conda environment allows you to specify a specific
version of Python and set of libraries. Open a terminal window in the directory
where you want to work.

Create a minimal environment with only Python installed in it.

.. code:: sh

  conda create -n name_of_my_env python=3


.. code:: sh

  source activate name_of_my_env

Or, if you're using Windows

1. Install Anaconda
2. Search for Anaconda Prompt
3. Open Anaconda Prompt

Use the following commands

.. code:: sh

  conda create -n name_of_my_env python=3

.. code:: sh

  activate name_of_my_env

Next, install the Qiskit package, which includes Terra, Aer, Ignis, and Aqua.

.. code:: sh

  pip install qiskit

If the packages installed correctly, you can run ``conda list`` to see the active
packages in your virtual environment.

.. note::

  When upgrading from Qiskit < 0.7 to the latest version, uninstall the old
  version of Qiskit with ``pip uninstall qiskit`` and then install the latest version.

There are optional dependencies that are required to use all the visualization
functions available in Qiskit. You can install these optional
dependencies by with the following command

.. code:: sh

  pip install qiskit-terra[visualization]

After you've installed and verified the Qiskit packages you want to use, import
them into your environment with Python to begin working.

.. code:: python

  import qiskit

.. _install_access_ibm_q_devices_label:

.. note::
  If you want to contribute to the Qiskit community by developing and contributing code
  with the most recently updated Qiskit code, see :ref:`Build Qiskit packages from source <install_install_from_source_label>`.


Access IBM Q Systems
--------------------

IBM Q offers several real quantum computers and high-performance classical
computing simulators through its IBM Q Experience with Qiskit. Follow
these steps to set up your Qiskit environment to send jobs to IBM Q systems.

.. note::

  With the release of Qiskit 0.11, if you had previously saved your IBM Q credentials locally, you
  might need to update your IBM Q Experience credentials so that you can use the new IBM Q
  Experience V2. See `Updating your IBM Q Experience Credentials
  <https://github.com/Qiskit/qiskit-ibmq-provider/#updating-your-ibm-q-experience-credentials>`__.

To configure your account, you create a local configuration file which includes an API key

**1.** `Create a free IBM Q Experience account <https://quantum-computing.ibm.com/login>`__.

**2.**  Navigate to **My Account** to view your account settings.

.. image:: /images/figures/install_0.png
   :alt: Image of where to find the section 'My accounts'.

**3.** Click on **Copy token** to copy the token to your clipboard.
Temporarily paste this API token into your favorite text editor so you can use it later to create
an account configuration file.

.. image:: /images/figures/install_1.png
   :alt: Image of where to get an API token.

**4.** Run the following commands to store your API token locally for later use in a
configuration file called ``qiskitrc``. Replace ``MY_API_TOKEN`` with the API token value that you
stored in your text editor.

.. code:: python

  from qiskit import IBMQ
  IBMQ.save_account('MY_API_TOKEN')


For more details, such as how to manage multiple IBM Q account credentials,
refer to this tutorial titled `The IBM Q Account
<https://github.com/Qiskit/qiskit-tutorials/blob/master/qiskit/fundamentals/3_the_ibmq_account.ipynb>`__.


Checking Which Version is Installed
-----------------------------------

Since the Qiskit package includes a constellation of different elements,
simply printing the version by running ``qiskit.__version__`` can be misleading as it
returns only the version for the ``qiskit-terra`` package. This is because
the ``qiskit`` namespace in Python doesn't come from the Qiskit package, but
instead is part of the ``qiskit-terra`` package.

.. jupyter-execute::

   import qiskit
   qiskit.__version__


To see the versions of all the Qiskit elements in your environment you can use
the ``__qiskit_version__`` attribute.
For example, running the following command will return a dictionary
that includes the versions for each of the installed Qiskit packages.

.. jupyter-execute::

   qiskit.__qiskit_version__


.. tip::
   If you're filing an issue or need to share your installed Qiskit versions for
   something, use the ``__qiskit_version__`` attribute.
