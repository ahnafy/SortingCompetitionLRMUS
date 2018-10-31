Tried to not check the last few characters if they can't make a longer lrmus in "findBest",
but it made no change

changed updateAt so that the string toMatch is always at least as long as the current lrmus, which saved
about 100ms
