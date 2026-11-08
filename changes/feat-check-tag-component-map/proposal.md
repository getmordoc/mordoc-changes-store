# Catch missing components

## Description
As a Mordoc contributor, I want Mordoc's development checks to fail when a content tag points to a component that doesn't exist, so that a typo or forgotten registration is caught while developing and doesn't silently show nothing.

## Why
- Nothing checks that a content tag points to a component that exists.
- The two lists of components have already grown apart (see [diagrams on landing pages](../fix-landing-diagram-component/proposal.md)).

## What
- Development checks that fail when a content tag points to a missing component.
- This is easier after [clearer code structure](../refactor-src-structure/proposal.md), but doesn't depend on it.
