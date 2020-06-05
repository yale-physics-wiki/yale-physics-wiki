.. _tensors:

Tensors
=====================================

Tensors are arrays of numbers which have a certain transformation in different coordinate systems. In a way, they are the generalization of a vector. Before getting more specific, let's revisit the concept of vectors while intoducing some notation and paying extra attention to some specific properties of vectors.

3D Vectors
-------------

Let's focus on three dimensional vectors to be specific. Here's an important question to ponder; what is the difference between a vector and an array of numbers? There are a lot of ways to answer that question, but for our purpose, the important difference, the important difference to notice is that the array of numbers corresponding to a vector change in a certain way when that vector is rotated.

Let us consider a vector :math:`v`. Given a coordinate system of unit vectors, say :math:`\hat{x}`, :math:`\hat{y}`, and :math:`\hat{z}`, we can express the vector as the sum of its components with the associated unit vectors. We can label the components, the numbers of the array in this coordinate system, with superscripts.

.. math::

	v=v^x \hat{x} + v^y \hat{y} + v^z \hat{z}

Now, let us change the notation slightly, labeling the coordinates with numbers rather than letters:

.. math::

	v=v^1 \hat{x}_1 + v^2 \hat{x}_2 + v^3 \hat{x}_3

We can write this as a sum:

.. math::

	v=\sum_{i=1}^3 v^i \hat{x}_i

Now, we introduce the Einstein summation convention. This convention states that when an index appears twice in an expression, we interpret that as a sum over the range of values for that index. In this context, that means that when :math:`i` appears twice, we know that represents a sum over the numbers 1, 2, and 3. So, we can rewrite our expression for :math:`v`:

.. math::

	v=v^i \hat{x}_i

Now, let's talk about rotations. A rotation in three dimensions is really an operator that can apply to objects. For vectors, this operator acts as multiplication by a 3x3 matrix. But it's important to note that a rotation operator is not the same as a rotation matrix; it only appears that way when looking at vectors. If you have a scalar representing temperature, it doesn't change when rotating; in that case, the rotation operator is the identity. If you have a spin 1/2 particle represented by a spinor, the rotation operator can be expressed by multiplication of a 2x2 complex matrix. In a sense, the defining property of our vector is that it transforms by multiplication of the familiar rotation matrix under rotations.

Let us write this matrix as :math:`R`. We can also label the components of this matrix:

.. math::

	R = \begin{pmatrix} 
	R^1_{\ \ 1} & R^1_{\ \ 2} & R^1_{\ \ 3}\\
	R^2_{\ \ 1} & R^2_{\ \ 2} & R^2_{\ \ 3}\\
	R^3_{\ \ 1} & R^3_{\ \ 2} & R^3_{\ \ 3}\\
	\end{pmatrix}

Note that we can express matrix multiplication using our Einstein summation convention. For example, :math:`R v = R^i_{\ \ j} v^j \hat{x}_i`. The sum over :math:`j` is the sum over each element in a row, and the sum over :math:`i` is the sum over the three rows.

Another important point to make is that the vector itself doesn't change when rotated. After all, if you and me are facing each other, I might see a vector pointing left while you see a vector pointing to the right. We're seeing the same underlying vector, it's just that the components are different since we're using different coordinate systems.

Let's call the rotated vector :math:`v'`. So, the defining properties of our vector (the underlying object doesn't change under rotations, and rotations are represented by our :math:`R` matrix) can be written as:

.. math::

	v = v^i \hat{x}_i = R^i_{\ \ j} v^j \hat{x}_i = v'

We can see that the \hat{x}_i is the same in both expressions, so to focus on the interesting properties, we can leave it out. Ignoring the unit vectors is a very common convention; it saves a lot of writing, but it's good to remember that the unit vectors should still be there when you're talking about the underlying object.

.. math::

	v^i = R^i_{\ \ j} v^j

Let us again change notation. It will be useful to consider an original set of coordinates and a new set of coordinates. We'll represent the new set of coordinates with primes on the indices.

.. math::

	v^{i'} = R^{i'}_{\ \ j} v^j

This equation gives the transformation property for vectors. Anything object that satisfies the above equation is, by definition, a vector.

4-Vectors
-----------

The interesting part of a Lorentz transformation is the boost. That's the new, counterintuitive physics when you first learn of them. It's therefore easy to forget that Lorentz transformations include rotations. 4-vectors are what we get when we extend the previous section to work with Lorentz transformations rather than rotations.

The first thing to do is to define our coordinate unit vectors. We add a time-like unit vector, :math:`\hat{t}`, or :math:`\hat{x}_0`. As explained previously, we never really write out these unit vectors, but they can be useful to think about.

Now, it's again time to introduce more notation. When we have an index ranging over 0, 1, 2, and 3, we will use a greek letter, like :math:`\mu, \nu,` etc. When we have an index ranging over just 1, 2, and 3 (the spatial components), we will use a latin letter, like :math:`i, j,` etc.

So, we commonly write a 4-vector as :math:`v=v^\mu \hat{x}_\mu`, or, since we often neglect the unit vectors, just writing the vector as :math:`v^\mu`.

We often write the 4x4 matrix associated with a Lorentz trasformation as :math:`\Lambda`. We label the components of this matrix:

.. math::

	\Lambda = \begin{pmatrix} 
	\Lambda^1_{\ \ 1} & \Lambda^1_{\ \ 2} & \Lambda^1_{\ \ 3} & \Lambda^1_{\ \ 4}\\
	\Lambda^2_{\ \ 1} & \Lambda^2_{\ \ 2} & \Lambda^2_{\ \ 3} & \Lambda^2_{\ \ 4}\\
	\Lambda^3_{\ \ 1} & \Lambda^3_{\ \ 2} & \Lambda^3_{\ \ 3} & \Lambda^3_{\ \ 4}\\
	\Lambda^4_{\ \ 1} & \Lambda^4_{\ \ 2} & \Lambda^4_{\ \ 3} & \Lambda^4_{\ \ 4}\\
	\end{pmatrix}

In the same way that rotations gave the defining property of 3D vectors, Lorentz transformations give the defining property of 4-vectors:

.. math::

	v^{\mu'} = \Lambda^{\mu'}_{\ \ \nu} v^\nu

So, not just any object with a timelike component and three spacelike components is a 4-vector. An object has to satisfy this rule for it to be a 4-vector. 

Definition of a Tensor
----------

A tensor, in the context of special relativity, is an object which transforms under Lorentz tranformations in a similar way as described above. Specifically, a tensor :math:`T` is a set of components which transforms in the following way:

.. math::

	T^{\mu_1'\dots \mu_k'}_{\qquad \ \ \nu_1' \dots \nu_k'} = \Lambda^{\mu_1'}_{\ \ \ \ \ \mu_1} \Lambda^{\mu_1'}_{\ \ \ \ \ \mu_1} \dots \Lambda^{\mu_k'}_{\ \ \ \ \ \mu_k} \Lambda^{\nu_1}_{\ \ \ \ \ \nu_1'} \dots \Lambda^{\nu_k}_{\ \ \ \ \ \nu_k'} T^{\mu_1\dots \mu_k}_{\qquad \ \ \nu_1 \dots \nu_k}

So, there is one Lorentz transformation matrix for each component that is getting changed to a new coordinate system. Note that the dummy indices (the indices being summed over in the Einstein summation convention) come in pairs of one raised and one lowered, and also note that any other index either stays raised or stays lowered. Remembering those simple rules makes this formula very easy to memorize in practice.

Checking with this definition, we see that a 4-vector is a tensor. Also, a scalar value (like a temperature) is a tensor, since it has no indices and also no Lorentz transformation matrices, so it also satisfies this definition. We can also see from this definition that any combinations like :math:`T^\mu S^\nu` are tensors if :math:`T` and :math:`S` are tensors.

Raising and Lowering
-------------------------













